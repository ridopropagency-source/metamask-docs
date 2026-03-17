# PR Review: Smart Accounts Kit Documentation Style Alignment

**Date:** March 17, 2026  
**Reviewer:** Cloud Agent  
**Style Guide Reference:** https://docs-template.consensys.io/contribute/style-guide

## PRs Under Review

1. **PR #2768** - [Smart Accounts Kit][Troubleshooting Section] Add invalid signature
   - URL: https://github.com/MetaMask/metamask-docs/pull/2768
   - Files: `smart-accounts-kit/troubleshooting/invalid-signature.md` (new)

2. **PR #2766** - [Smart Accounts Kit][Troubleshoot] Invalid Delegator  
   - URL: https://github.com/MetaMask/metamask-docs/pull/2766
   - Files: `smart-accounts-kit/troubleshooting/invalid-delegator.md` (new)

---

## Overall Assessment

Both PRs add troubleshooting documentation for error codes in the Smart Accounts Kit. The content is generally well-written and aligned with the Consensys style guide, but there are several areas for improvement.

---

## PR #2768: Invalid Signature Troubleshooting

### ✅ Strengths

1. **Well-organized content** - Clear structure with distinct problem scenarios
2. **Developer-focused** - Includes practical code samples
3. **Scannable content** - Good use of headings and sections
4. **Sentence case headings** - Properly follows formatting guidelines

### ⚠️ Issues & Recommendations

#### 1. **Conversational Tone - Use Contractions**

**Location:** Multiple places in the document  
**Issue:** The document doesn't use common contractions, making it less conversational.

**Current:**
```markdown
If the smart account has not been deployed yet, it has no code at its address,
so the Delegation Manager treats it as an EOA and attempts ECDSA signature recovery.
```

**Recommended:**
```markdown
If the smart account hasn't been deployed yet, it has no code at its address,
so the Delegation Manager treats it as an EOA and attempts ECDSA signature recovery.
```

**Other instances:**
- "has not been deployed" → "hasn't been deployed"
- "do not match" → "don't match"
- "will not match" → "won't match"

---

#### 2. **Passive Voice Usage**

**Location:** Line 12-13  
**Issue:** Uses passive voice instead of active voice.

**Current:**
```markdown
The root delegation's delegator must be a MetaMask smart account. The Delegation Manager
checks delegator code length to determine whether the delegator is an EOA or a smart account.
```

**Recommended:**
```markdown
The root delegation's delegator must be a MetaMask smart account. The Delegation Manager
checks the delegator code length to determine whether the delegator is an EOA or a smart account.
```

---

#### 3. **Clarity and Conciseness**

**Location:** Lines 62-65  
**Issue:** Sentence could be more concise and direct.

**Current:**
```markdown
The delegation was signed with an account that does not correspond to the delegator
address. When the delegator is an EOA, the Delegation Manager recovers the signer from
the EIP-712 typed data hash and compares it to the `delegator` field. If they do not
match, the transaction reverts.
```

**Recommended:**
```markdown
The delegation was signed with an account that doesn't correspond to the delegator
address. When the delegator is an EOA, the Delegation Manager recovers the signer from
the EIP-712 typed data hash and compares it to the `delegator` field. If they don't
match, the transaction reverts.
```

---

#### 4. **Code Comment Clarity**

**Location:** Lines 44-48  
**Issue:** Comments in code sample are lengthy and could be more concise.

**Current:**
```typescript
  // The address to which EOA has delegated. According to EIP-7702, 0xef0100 || address
  // represents the delegation. 
  // 
  // You need to remove the first 8 characters (0xef0100) to get the delegator address.
  const delegatorAddress = `0x${code.substring(8)}`;
```

**Recommended:**
```typescript
  // According to EIP-7702, the code format is 0xef0100 || address.
  // Remove the first 8 characters (0xef0100) to get the delegator address.
  const delegatorAddress = `0x${code.substring(8)}`;
```

---

#### 5. **Inconsistent Terminology**

**Location:** Line 51  
**Issue:** Mix of "upgrade" terminology.

**Current:**
```markdown
  // If account is not upgraded to MetaMask smart account, you can
```

**Recommended:**
```markdown
  // If the account isn't upgraded to a MetaMask smart account, you can
```

---

#### 6. **Link Text Improvement**

**Location:** Line 56  
**Issue:** Link text could be more descriptive.

**Current:**
```markdown
If the EOA is not upgraded to MetaMask smart account, [learn how to upgrade an EOA to MetaMask smart account](../get-started/smart-account-quickstart/eip7702.md).
```

**Recommended:**
```markdown
If the EOA isn't upgraded to a MetaMask smart account, see the [EIP-7702 quickstart guide](../get-started/smart-account-quickstart/eip7702.md).
```

---

#### 7. **Article Usage**

**Location:** Multiple places  
**Issue:** Missing article "a" before "MetaMask smart account".

**Current:**
```markdown
If the EOA is not upgraded to MetaMask smart account
```

**Recommended:**
```markdown
If the EOA isn't upgraded to a MetaMask smart account
```

---

#### 8. **Typo in Implementation Name**

**Location:** Line 49  
**Issue:** "DeleGator" appears to have incorrect capitalization.

**Current:**
```typescript
  .EIP7702StatelessDeleGatorImpl;
```

**Verify:** Is this the correct spelling/capitalization of the implementation name? If it's a typo in the codebase reference, it should be corrected. If it's the actual name, it should remain as-is.

---

## PR #2766: Invalid Delegator Troubleshooting

### ✅ Strengths

1. **Clear and concise** - Gets to the point quickly
2. **Good code example** - Practical TypeScript sample
3. **Proper formatting** - Sentence case headings, code formatting for references
4. **Scannable content** - Well-structured with clear sections

### ⚠️ Issues & Recommendations

#### 1. **Conversational Tone - Use Contractions**

**Location:** Multiple places  
**Issue:** Missing contractions throughout.

**Examples to fix:**
- "is not the delegator" → "isn't the delegator"
- "has not been deployed" → "hasn't been deployed"

---

#### 2. **Error Code Reference Typo**

**Location:** error-codes.md, line 18  
**Issue:** Spelling error in table.

**Current:**
```markdown
The caller is not the delegator specificed in the delegation.
```

**Recommended:**
```markdown
The caller isn't the delegator specified in the delegation.
```

(Also adds contraction per style guide)

---

#### 3. **Grammar and Article Usage**

**Location:** Line 17  
**Issue:** Missing article.

**Current:**
```markdown
Verify that the transaction is sent from the delegator's account. If the delegator is a smart account, submit an user operation through the smart account.
```

**Recommended:**
```markdown
Verify that the transaction is sent from the delegator's account. If the delegator is a smart account, submit a user operation through the smart account.
```

---

#### 4. **Passive Voice**

**Location:** Line 16-17  
**Issue:** Could be more direct with active voice.

**Current:**
```markdown
Verify that the transaction is sent from the delegator's account.
```

**Recommended:**
```markdown
Verify that you're sending the transaction from the delegator's account.
```

---

#### 5. **Code Comment Spacing**

**Location:** Line 23  
**Issue:** Comment formatting could be cleaner.

**Current:**
```typescript
const disableCalldata = DelegationManager.encode.disableDelegation({
  // Signed delegation from delegatorSmartAccount.
  delegation: signedDelegation,
});
```

**Recommended:**
```typescript
// Generate calldata to disable the delegation.
const disableCalldata = DelegationManager.encode.disableDelegation({
  delegation: signedDelegation, // Signed by delegatorSmartAccount
});
```

---

## Common Issues Across Both PRs

### 1. **Lack of Contractions**
Both documents avoid contractions, which makes them less conversational than the style guide recommends. This is the most significant deviation from the style guide.

**Style Guide Reference:**
> Use common contractions, such as "it's" and "you're," as if you're speaking to the reader.

### 2. **Article Usage**
Both PRs occasionally omit articles ("a", "the") where they should be included, particularly before "MetaMask smart account" and "user operation."

### 3. **Consistent Terminology**
Ensure consistent use of:
- "smart account" (not switching between "smart account" and "MetaMask smart account" without clarity)
- "user operation" (with article "a")
- "delegator" vs "delegator's"

---

## Style Guide Compliance Scorecard

### PR #2768: Invalid Signature

| Criterion | Score | Notes |
|-----------|-------|-------|
| Organize content by function | ✅ Excellent | Well-structured how-to/troubleshooting guide |
| Use conversational tone | ⚠️ Needs work | Lacks contractions, some passive voice |
| Write for developers | ✅ Good | Includes code samples and prerequisites |
| Create scannable content | ✅ Good | Well-organized with clear sections |
| Format text properly | ✅ Good | Proper sentence case, code formatting |
| **Overall** | **7/10** | Strong content, needs tone adjustments |

### PR #2766: Invalid Delegator

| Criterion | Score | Notes |
|-----------|-------|-------|
| Organize content by function | ✅ Excellent | Clear, focused troubleshooting content |
| Use conversational tone | ⚠️ Needs work | Lacks contractions, minor passive voice |
| Write for developers | ✅ Good | Practical code example included |
| Create scannable content | ✅ Excellent | Concise and well-structured |
| Format text properly | ⚠️ Good | One typo in referenced file |
| **Overall** | **7.5/10** | Strong, concise content with minor issues |

---

## Priority Recommendations

### High Priority (Should Fix)

1. **Add contractions throughout both documents** - This is a key style guide requirement
2. **Fix typo in PR #2766** - "specificed" → "specified"
3. **Add missing articles** - "an user operation" → "a user operation"
4. **Verify "DeleGatorImpl" spelling** in PR #2768

### Medium Priority (Should Consider)

1. **Convert passive voice to active** where appropriate
2. **Simplify code comments** for better readability
3. **Make link text more descriptive**

### Low Priority (Nice to Have)

1. **Further condense lengthy sentences** for scannability
2. **Standardize terminology** references throughout

---

## Conclusion

Both PRs provide valuable troubleshooting documentation that is well-organized and developer-focused. The main area for improvement is adopting a more conversational tone through the use of contractions, as recommended by the Consensys style guide. With these adjustments, the content will better match the overall Smart Accounts Kit documentation style.

The content demonstrates strong technical accuracy and practical guidance. After addressing the high-priority recommendations, these pages will be excellent additions to the troubleshooting section.
