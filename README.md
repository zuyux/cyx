# CYX

CYX is a synthetic basket token that aggregates the top 50 native cryptocurrencies into a single, diversified asset. Built on Rootstock (RSK) using Solidity, CYX fetches Chainlink oracles for real-time price and market capitalization data, calculates its Net Asset Value (NAV), and processes minting and burning operations. The token’s governance is planned to be managed by a decentralized autonomous organization (DAO), with 50% of resources earmarked for Research & Development in distributed systems, cryptography, P2P protocols, computing, and general science.

## Features

- **Diversified Exposure:**  
  CYX represents a basket of 50 native cryptocurrencies, non-stablecoins, reducing unsystematic risk and offering broad market exposure in one token.

- **Real-Time Data via Chainlink:**  
  The contract fetches price and market cap data from Chainlink oracles to ensure that NAV calculations reflect the latest market conditions.

- **Dynamic Weighting and Rebalancing:**  
  Each asset's contribution is determined by its market capitalization. A weight cap (e.g., 20%) is enforced to prevent any single asset from dominating the index. Excess weight is redistributed proportionally among uncapped assets, maintaining overall diversification.

- **Minting and Burning Mechanics:**  
  - **Minting:** Users can mint CYX tokens by depositing assets. The number of tokens minted is based on the deposit amount divided by the current NAV.
  - **Burning:** Users can redeem their CYX tokens by burning them; the redemption value is calculated as the number of tokens burned multiplied by the current NAV.
  
- **Governance:**  
  A DAO will oversee protocol upgrades, rebalancing strategies, and fund allocation (including the 50% for R&D), ensuring transparent and community-driven decision-making.

## Contract Architecture

### Key Components

1. **Chainlink Oracle Integration:**
   - **Price Feeds:** Fetches the current price $(P_i(t)\)$ for each of the 50 assets.
   - **Market Cap Feeds:** Retrieves up-to-date market capitalization data $(\text{MC}_i(t)\)$ for each asset.

2. **NAV Calculation:**
   The NAV is computed using the formula:
   
$$
{NAV}_{{CYX}}(t) = \sum{i=1}^{50} w_i(t) \times P_i(t)
$$
   
   where $(w_i(t)\)$ is the weight of asset $(i\)$ calculated from its market cap.

4. **Weight Management:**
   - Preliminary weight for each asset:
     
$$
w'_i = \frac{{MC}i}{\sum{j=1}^{50} {MC}_j}
$$
     
   - Apply a cap (e.g., 20%) and redistribute any excess weight proportionally to uncapped assets, ensuring:
     
$$
\sum_{i=1}^{50} w_i = 1
$$

5. **Minting and Burning Functions:**
   - **Minting:**

$$
\Delta \text{CYX} = \frac{D}{\text{NAV}_{\text{CYX}}(t)}
$$

   Where $(D\)$ is the deposit amount.
   - **Burning:**

$$
\text{Redemption Value} = \Delta \text{CYX} \times \text{NAV}_{\text{CYX}}(t)
$$

   Where $(\Delta \text{CYX}\)$ is the number of tokens burned.
     

## Usage

- **Minting CYX:**  
  Users deposit assets via the mint function. The contract fetches the latest data, calculates the NAV, and mints tokens proportionally.
  
- **Burning CYX:**  
  Users redeem their tokens by calling the burn function, receiving an asset value based on the current NAV.

- **Rebalancing:**  
  The contract’s rebalancing logic periodically recalculates weights and NAV, ensuring the basket remains diversified and aligned with market dynamics.

## Governance and Future Enhancements

CYX is designed to be governed by a DAO that will oversee:
- Protocol upgrades and rebalancing strategies.
- Allocation of 50% of resources to R&D.
- Community-driven proposals and voting mechanisms.

Future updates may include enhanced off-chain computation, advanced scaling solutions (e.g., zk-rollups), and tighter integration with decentralized finance (DeFi) platforms.

## Security Considerations

- **Smart Contract Audits:**  
  All contracts are to be audited by reputable security firms to prevent vulnerabilities.

- **Oracle Data Integrity:**  
  The integration with Chainlink ensures decentralized and tamper-resistant data feeds.

- **Fail-Safe Mechanisms:**  
  Implement emergency stop functions and fallback protocols in case of data discrepancies or unexpected events.

## License

This project is licensed under the [MIT License](LICENSE).

## Contributing

Contributions are welcome! Please refer to [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on submitting pull requests and bug reports.

## Contact

For further inquiries or support, please contact [40230@pm.me](mailto:40230@pm.me).
