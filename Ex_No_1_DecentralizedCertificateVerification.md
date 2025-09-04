# Experiment 1: Decentralized Certificate Verification
## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Program:
### Name: Masina Sree Karsh
### Register Number : 212223100033

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree, uint256 year) public {
require(msg.sender == university, "Only university can issue certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree, uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
return certificates[certHash];
}
}
```
## Expected Output:
```
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```
## Output:

<img width="1917" height="982" alt="Screenshot 2025-09-04 061510" src="https://github.com/user-attachments/assets/83a83b5c-65e7-4f8f-be3f-b88b2cce7b24" />

<img width="1909" height="988" alt="Screenshot 2025-09-04 061242" src="https://github.com/user-attachments/assets/5d2f6603-88a3-470d-9e01-bad51186649e" />



## Result:
Thus, to develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity is done successfully.
