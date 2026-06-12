---
title: "Segmentation fault using smartcard - pkcs11-tool"
date: 2009-11-18
forum: General Help
---

### Post by deyandeyan on 2009-11-18
hi there, 

I use ubuntu 9.10 x86 with Linux 2.6.31-14-generic-pae. The issue appears with generic kernel without pae. 

I have an omnikey usb smartcard reader. 

When I try to do 

pkcs11-tool --test --login 
I get an error: 

pkcs11-tool[4368]: segfault at 0 ip b73e0c16 sp bff17bd0 error 4 in opensc-pkcs11.so[b73d6000+14000]

The debug output from opensc is at the bottom of the message.
Everything used to work until I upgraded to 9.10. Then I did a clean install - same issue. I tested on another pc - same issue. Has anybody experienced the same  problem ?

Thanks , 
Deyan 

-------------------


$ pkcs11-tool --test --login[opensc-pkcs11] ctx.c:730:sc_context_create: ===================================
[opensc-pkcs11] ctx.c:731:sc_context_create: opensc version: 0.11.8
[opensc-pkcs11] reader-pcsc.c:879:pcsc_detect_readers: Probing pcsc readers
[opensc-pkcs11] reader-pcsc.c:901:pcsc_detect_readers: Establish pcsc context
[opensc-pkcs11] reader-pcsc.c:951:pcsc_detect_readers: Found new pcsc reader 'OmniKey CardMan 6121 00 00'
[opensc-pkcs11] slot.c:86:card_detect: 0: Detecting smart card
[opensc-pkcs11] sc.c:196:sc_detect_card_presence: called
[opensc-pkcs11] sc.c:201:sc_detect_card_presence: returning with: 1
[opensc-pkcs11] slot.c:126:card_detect: 0: Connecting to smart card
[opensc-pkcs11] card.c:110:sc_connect_card: called
[opensc-pkcs11] reader-pcsc.c:532:pcsc_connect: After connect protocol = 2
[opensc-pkcs11] reader-pcsc.c:551:pcsc_connect: Requesting reader features ... 
[opensc-pkcs11] card-rutoken.c:129:rutoken_match_card: called
[opensc-pkcs11] card-rutoken.c:135:rutoken_match_card: returning with: 0
[opensc-pkcs11] card-cardos.c:79:cardos_match_card: checking cardos version ...
[opensc-pkcs11] card-cardos.c:97:cardos_match_card: found cardos v4.3b
[opensc-pkcs11] card.c:221:sc_connect_card: card info: CardOS M4, 1004, 0x0
[opensc-pkcs11] card.c:222:sc_connect_card: returning with: 0
[opensc-pkcs11] slot.c:134:card_detect: 0: Detecting Framework
[opensc-pkcs11] pkcs15.c:700:sc_pkcs15_bind: called
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f002f00
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:259:cardos_check_sw: file not found
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: -1201
[opensc-pkcs11] card.c:554:sc_select_file: returning with: -1201
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f005015
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f0050155031
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] pkcs15.c:623:sc_pkcs15_bind_internal: The following DFs were found:
[opensc-pkcs11] pkcs15.c:633:sc_pkcs15_bind_internal:   DF type 0, path 3f0050154400, index 0, count -1
[opensc-pkcs11] pkcs15.c:633:sc_pkcs15_bind_internal:   DF type 1, path 3f0050154401, index 0, count -1
[opensc-pkcs11] pkcs15.c:633:sc_pkcs15_bind_internal:   DF type 4, path 3f0050154404, index 0, count -1
[opensc-pkcs11] pkcs15.c:633:sc_pkcs15_bind_internal:   DF type 7, path 3f0050154407, index 0, count -1
[opensc-pkcs11] pkcs15.c:633:sc_pkcs15_bind_internal:   DF type 8, path 3f0050154408, index 0, count -1
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f0050155032
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] framework-pkcs15.c:159:pkcs15_bind: Binding to PKCS#15, rc=0
[opensc-pkcs11] slot.c:148:card_detect: 0: Detected framework 0. Creating tokens.
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f0050154408, index=0, count=-1
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f0050154408
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:259:cardos_check_sw: record not found
[opensc-pkcs11] framework-pkcs15.c:734:pkcs15_create_tokens: Found 3 authentication objects
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f0050154400, index=0, count=-1
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f0050154400
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:259:cardos_check_sw: record not found
[opensc-pkcs11] framework-pkcs15.c:453:pkcs15_create_pkcs11_objects: Found 4 private keys
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f0050154401, index=0, count=-1
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f0050154401
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:259:cardos_check_sw: record not found
[opensc-pkcs11] framework-pkcs15.c:453:pkcs15_create_pkcs11_objects: Found 4 public keys
[opensc-pkcs11] pkcs15-pubkey.c:387:sc_pkcs15_read_pubkey: called
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f00501550754b01, index=0, count=-1
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550754b01
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] pkcs15-pubkey.c:387:sc_pkcs15_read_pubkey: called
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f00501550754b02, index=0, count=-1
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550754b02
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] pkcs15-pubkey.c:387:sc_pkcs15_read_pubkey: called
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f00501550754b03, index=0, count=-1
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550754b03
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] pkcs15-pubkey.c:387:sc_pkcs15_read_pubkey: called
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f00501550754b04, index=0, count=-1
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550754b04
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f0050154404, index=0, count=-1
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f0050154404
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:259:cardos_check_sw: record not found
[opensc-pkcs11] framework-pkcs15.c:453:pkcs15_create_pkcs11_objects: Found 2 certificates
[opensc-pkcs11] pkcs15-cert.c:115:sc_pkcs15_read_certificate: called
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f00501543044301, index=0, count=1798
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501543044301
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] pkcs15-cert.c:115:sc_pkcs15_read_certificate: called
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f00501543044302, index=0, count=1942
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501543044302
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] pkcs15.c:1672:sc_pkcs15_read_file: called, path=3f0050154407, index=0, count=-1
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f0050154407
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:259:cardos_check_sw: record not found
[opensc-pkcs11] framework-pkcs15.c:453:pkcs15_create_pkcs11_objects: Found 0 data objects
[opensc-pkcs11] slot.c:235:slot_allocate: Allocated slot 0
[opensc-pkcs11] framework-pkcs15.c:693:pkcs15_init_slot: Initialized token 'InfoNotary (PIN)'
[opensc-pkcs11] framework-pkcs15.c:800:pkcs15_create_tokens: Adding private key 0 to PIN 0
[opensc-pkcs11] framework-pkcs15.c:800:pkcs15_create_tokens: Adding private key 1 to PIN 0
[opensc-pkcs11] framework-pkcs15.c:800:pkcs15_create_tokens: Adding private key 2 to PIN 0
[opensc-pkcs11] framework-pkcs15.c:800:pkcs15_create_tokens: Adding private key 3 to PIN 0
[opensc-pkcs11] slot.c:235:slot_allocate: Allocated slot 1
[opensc-pkcs11] framework-pkcs15.c:693:pkcs15_init_slot: Initialized token 'InfoNotary (Secondary Authentication PIN)'
[opensc-pkcs11] slot.c:235:slot_allocate: Allocated slot 2
[opensc-pkcs11] slot.c:235:slot_allocate: Allocated slot 3
[opensc-pkcs11] framework-pkcs15.c:851:pkcs15_create_tokens: All tokens created
[opensc-pkcs11] slot.c:156:card_detect: 0: Detection ended
[opensc-pkcs11] pkcs11-global.c:232:C_Initialize: C_Initialize: result = 0
[opensc-pkcs11] pkcs11-global.c:349:C_GetSlotList: Getting slot listing
[opensc-pkcs11] reader-pcsc.c:879:pcsc_detect_readers: Probing pcsc readers
[opensc-pkcs11] slot.c:86:card_detect: 0: Detecting smart card
[opensc-pkcs11] sc.c:196:sc_detect_card_presence: called
[opensc-pkcs11] sc.c:201:sc_detect_card_presence: returning with: 1
[opensc-pkcs11] slot.c:156:card_detect: 0: Detection ended
[opensc-pkcs11] pkcs11-global.c:365:C_GetSlotList: was only a size inquiry (16)
[opensc-pkcs11] pkcs11-global.c:349:C_GetSlotList: Getting slot listing
[opensc-pkcs11] slot.c:86:card_detect: 0: Detecting smart card
[opensc-pkcs11] sc.c:196:sc_detect_card_presence: called
[opensc-pkcs11] sc.c:201:sc_detect_card_presence: returning with: 1
[opensc-pkcs11] slot.c:156:card_detect: 0: Detection ended
[opensc-pkcs11] pkcs11-global.c:382:C_GetSlotList: returned 16 slots
[opensc-pkcs11] pkcs11-session.c:40:C_OpenSession: Opening new session for slot 0
[opensc-pkcs11] pkcs11-global.c:471:C_GetTokenInfo: Getting info about token in slot 0
Please enter User PIN: 
[opensc-pkcs11] pkcs11-session.c:239:C_Login: Login for session 1
[opensc-pkcs11] framework-pkcs15.c:929:pkcs15_login: PIN verification returned 0
C_SeedRandom() and C_GenerateRandom():
[opensc-pkcs11] pkcs11-session.c:40:C_OpenSession: Opening new session for slot 0
  seeding (C_SeedRandom) not supported
  seems to be OK
Digests:
[opensc-pkcs11] pkcs11-session.c:40:C_OpenSession: Opening new session for slot 0
[opensc-pkcs11] pkcs11-object.c:391:C_DigestInit: C_DigestInit returns 0
[opensc-pkcs11] pkcs11-object.c:439:C_DigestUpdate: C_DigestUpdate returns 0
[opensc-pkcs11] pkcs11-object.c:439:C_DigestUpdate: C_DigestUpdate returns 0
[opensc-pkcs11] pkcs11-object.c:439:C_DigestUpdate: C_DigestUpdate returns 0
[opensc-pkcs11] pkcs11-object.c:465:C_DigestFinal: C_DigestFinal returns 0
[opensc-pkcs11] pkcs11-object.c:391:C_DigestInit: C_DigestInit returns 0
[opensc-pkcs11] pkcs11-object.c:418:C_Digest: C_Digest returns 0
  all 4 digest functions seem to work
[opensc-pkcs11] pkcs11-object.c:391:C_DigestInit: C_DigestInit returns 0
  MD5: [opensc-pkcs11] pkcs11-object.c:418:C_Digest: C_Digest returns 0
OK
[opensc-pkcs11] pkcs11-object.c:391:C_DigestInit: C_DigestInit returns 0
  SHA-1: [opensc-pkcs11] pkcs11-object.c:418:C_Digest: C_Digest returns 0
OK
[opensc-pkcs11] pkcs11-object.c:391:C_DigestInit: C_DigestInit returns 0
  RIPEMD160: [opensc-pkcs11] pkcs11-object.c:418:C_Digest: C_Digest returns 0
OK
[opensc-pkcs11] pkcs11-object.c:391:C_DigestInit: C_DigestInit returns 0
[opensc-pkcs11] pkcs11-object.c:418:C_Digest: C_Digest returns 336
[opensc-pkcs11] pkcs11-object.c:418:C_Digest: C_Digest returns 0
[opensc-pkcs11] pkcs11-object.c:418:C_Digest: C_Digest returns 0
[opensc-pkcs11] pkcs11-session.c:131:C_CloseSession: C_CloseSession(3)
[opensc-pkcs11] pkcs11-session.c:40:C_OpenSession: Opening new session for slot 0
[opensc-pkcs11] pkcs11-session.c:179:C_GetSessionInfo: C_GetSessionInfo(slot 0).
Signatures (currently only RSA signatures)
[opensc-pkcs11] pkcs11-object.c:237:C_FindObjectsInit: C_FindObjectsInit(slot = 0)
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_CLASS = CKO_PRIVATE_KEY
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/1 matches
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/4 matches
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/6 matches
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/8 matches
[opensc-pkcs11] pkcs11-object.c:307:C_FindObjectsInit: 4 matching objects
  testing key 0 [opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_LABEL = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_LABEL = 0E81EEDA-0A6A-40FC-880B-0351F9EA7C7E
(0E81EEDA-0A6A-40FC-880B-0351F9EA7C7E) [opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_SIGN = TRUE

[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:237:C_FindObjectsInit: C_FindObjectsInit(slot = 0)
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_CLASS = CKO_PUBLIC_KEY
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/3 matches
[opensc-pkcs11] pkcs11-object.c:307:C_FindObjectsInit: 1 matching objects
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_MODULUS_BITS = 0x400
[opensc-pkcs11] pkcs11-object.c:512:C_SignInit: Sign initialization returns 0
[opensc-pkcs11] pkcs11-object.c:574:C_SignUpdate: C_SignUpdate returns 0
[opensc-pkcs11] pkcs11-object.c:574:C_SignUpdate: C_SignUpdate returns 0
[opensc-pkcs11] pkcs11-object.c:574:C_SignUpdate: C_SignUpdate returns 0
[opensc-pkcs11] framework-pkcs15.c:2048:pkcs15_prkey_sign: Initiating signing operation, mechanism 0x3.
[opensc-pkcs11] framework-pkcs15.c:2104:pkcs15_prkey_sign: Selected flags 1. Now computing signature for 128 bytes. 1024 bytes reserved.
[opensc-pkcs11] pkcs15-sec.c:150:sc_pkcs15_compute_signature: called
[opensc-pkcs11] pkcs15-sec.c:73:sc_pkcs15_decipher: called
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550724b015501
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:751:cardos_set_security_env: returning with: 0
[opensc-pkcs11] framework-pkcs15.c:2124:pkcs15_prkey_sign: Sign complete. Result 128.
[opensc-pkcs11] pkcs11-object.c:610:C_SignFinal: C_SignFinal returns 0
[opensc-pkcs11] pkcs11-object.c:512:C_SignInit: Sign initialization returns 0
[opensc-pkcs11] framework-pkcs15.c:2048:pkcs15_prkey_sign: Initiating signing operation, mechanism 0x3.
[opensc-pkcs11] framework-pkcs15.c:2104:pkcs15_prkey_sign: Selected flags 1. Now computing signature for 128 bytes. 1024 bytes reserved.
[opensc-pkcs11] pkcs15-sec.c:150:sc_pkcs15_compute_signature: called
[opensc-pkcs11] pkcs15-sec.c:73:sc_pkcs15_decipher: called
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550724b015501
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:751:cardos_set_security_env: returning with: 0
[opensc-pkcs11] framework-pkcs15.c:2124:pkcs15_prkey_sign: Sign complete. Result 128.
[opensc-pkcs11] pkcs11-object.c:554:C_Sign: Signing result was 0
  all 4 signature functions seem to work
[opensc-pkcs11] pkcs11-object.c:512:C_SignInit: Sign initialization returns 0
[opensc-pkcs11] pkcs11-object.c:554:C_Sign: Signing result was 336
[opensc-pkcs11] pkcs11-object.c:554:C_Sign: Signing result was 0
[opensc-pkcs11] framework-pkcs15.c:2048:pkcs15_prkey_sign: Initiating signing operation, mechanism 0x3.
[opensc-pkcs11] framework-pkcs15.c:2104:pkcs15_prkey_sign: Selected flags 1. Now computing signature for 128 bytes. 128 bytes reserved.
[opensc-pkcs11] pkcs15-sec.c:150:sc_pkcs15_compute_signature: called
[opensc-pkcs11] pkcs15-sec.c:73:sc_pkcs15_decipher: called
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550724b015501
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:751:cardos_set_security_env: returning with: 0
[opensc-pkcs11] framework-pkcs15.c:2124:pkcs15_prkey_sign: Sign complete. Result 128.
[opensc-pkcs11] pkcs11-object.c:554:C_Sign: Signing result was 0
  testing signature mechanisms:
[opensc-pkcs11] pkcs11-object.c:512:C_SignInit: Sign initialization returns 0
    RSA-X-509: [opensc-pkcs11] framework-pkcs15.c:2048:pkcs15_prkey_sign: Initiating signing operation, mechanism 0x3.
[opensc-pkcs11] framework-pkcs15.c:2104:pkcs15_prkey_sign: Selected flags 1. Now computing signature for 128 bytes. 1024 bytes reserved.
[opensc-pkcs11] pkcs15-sec.c:150:sc_pkcs15_compute_signature: called
[opensc-pkcs11] pkcs15-sec.c:73:sc_pkcs15_decipher: called
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550724b015501
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:751:cardos_set_security_env: returning with: 0
[opensc-pkcs11] framework-pkcs15.c:2124:pkcs15_prkey_sign: Sign complete. Result 128.
[opensc-pkcs11] pkcs11-object.c:554:C_Sign: Signing result was 0
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:237:C_FindObjectsInit: C_FindObjectsInit(slot = 0)
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_CLASS = CKO_PUBLIC_KEY
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/3 matches
[opensc-pkcs11] pkcs11-object.c:307:C_FindObjectsInit: 1 matching objects
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_VALUE = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_VALUE = 308189028181008469765A7A6CFB6AD96CEE2EA15A85DBC7EA96595100AD91AC
OK
[opensc-pkcs11] pkcs11-object.c:512:C_SignInit: Sign initialization returns 0
    RSA-PKCS: [opensc-pkcs11] framework-pkcs15.c:2048:pkcs15_prkey_sign: Initiating signing operation, mechanism 0x1.
[opensc-pkcs11] framework-pkcs15.c:2104:pkcs15_prkey_sign: Selected flags 12. Now computing signature for 35 bytes. 1024 bytes reserved.
[opensc-pkcs11] pkcs15-sec.c:150:sc_pkcs15_compute_signature: called
[opensc-pkcs11] pkcs15-sec.c:73:sc_pkcs15_decipher: called
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550724b015501
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:751:cardos_set_security_env: returning with: 0
[opensc-pkcs11] framework-pkcs15.c:2124:pkcs15_prkey_sign: Sign complete. Result 128.
[opensc-pkcs11] pkcs11-object.c:554:C_Sign: Signing result was 0
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:237:C_FindObjectsInit: C_FindObjectsInit(slot = 0)
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_CLASS = CKO_PUBLIC_KEY
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/3 matches
[opensc-pkcs11] pkcs11-object.c:307:C_FindObjectsInit: 1 matching objects
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_VALUE = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_VALUE = 308189028181008469765A7A6CFB6AD96CEE2EA15A85DBC7EA96595100AD91AC
OK
[opensc-pkcs11] pkcs11-object.c:512:C_SignInit: Sign initialization returns 0
    SHA1-RSA-PKCS: [opensc-pkcs11] framework-pkcs15.c:2048:pkcs15_prkey_sign: Initiating signing operation, mechanism 0x6.
[opensc-pkcs11] framework-pkcs15.c:2104:pkcs15_prkey_sign: Selected flags 22. Now computing signature for 20 bytes. 1024 bytes reserved.
[opensc-pkcs11] pkcs15-sec.c:150:sc_pkcs15_compute_signature: called
[opensc-pkcs11] pkcs15-sec.c:73:sc_pkcs15_decipher: called
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550724b015501
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:751:cardos_set_security_env: returning with: 0
[opensc-pkcs11] framework-pkcs15.c:2124:pkcs15_prkey_sign: Sign complete. Result 128.
[opensc-pkcs11] pkcs11-object.c:554:C_Sign: Signing result was 0
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:237:C_FindObjectsInit: C_FindObjectsInit(slot = 0)
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_CLASS = CKO_PUBLIC_KEY
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/3 matches
[opensc-pkcs11] pkcs11-object.c:307:C_FindObjectsInit: 1 matching objects
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_VALUE = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_VALUE = 308189028181008469765A7A6CFB6AD96CEE2EA15A85DBC7EA96595100AD91AC
OK
[opensc-pkcs11] pkcs11-object.c:512:C_SignInit: Sign initialization returns 0
    MD5-RSA-PKCS: [opensc-pkcs11] framework-pkcs15.c:2048:pkcs15_prkey_sign: Initiating signing operation, mechanism 0x5.
[opensc-pkcs11] framework-pkcs15.c:2104:pkcs15_prkey_sign: Selected flags 42. Now computing signature for 16 bytes. 1024 bytes reserved.
[opensc-pkcs11] pkcs15-sec.c:150:sc_pkcs15_compute_signature: called
[opensc-pkcs11] pkcs15-sec.c:73:sc_pkcs15_decipher: called
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550724b015501
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:751:cardos_set_security_env: returning with: 0
[opensc-pkcs11] framework-pkcs15.c:2124:pkcs15_prkey_sign: Sign complete. Result 128.
[opensc-pkcs11] pkcs11-object.c:554:C_Sign: Signing result was 0
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:237:C_FindObjectsInit: C_FindObjectsInit(slot = 0)
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_CLASS = CKO_PUBLIC_KEY
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/3 matches
[opensc-pkcs11] pkcs11-object.c:307:C_FindObjectsInit: 1 matching objects
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_VALUE = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_VALUE = 308189028181008469765A7A6CFB6AD96CEE2EA15A85DBC7EA96595100AD91AC
OK
[opensc-pkcs11] pkcs11-object.c:512:C_SignInit: Sign initialization returns 0
    RIPEMD160-RSA-PKCS: [opensc-pkcs11] framework-pkcs15.c:2048:pkcs15_prkey_sign: Initiating signing operation, mechanism 0x8.
[opensc-pkcs11] framework-pkcs15.c:2104:pkcs15_prkey_sign: Selected flags 102. Now computing signature for 20 bytes. 1024 bytes reserved.
[opensc-pkcs11] pkcs15-sec.c:150:sc_pkcs15_compute_signature: called
[opensc-pkcs11] pkcs15-sec.c:73:sc_pkcs15_decipher: called
[opensc-pkcs11] card.c:532:sc_select_file: called; type=2, path=3f00501550724b015501
[opensc-pkcs11] card-cardos.c:431:cardos_select_file: called
[opensc-pkcs11] card-cardos.c:435:cardos_select_file: returning with: 0
[opensc-pkcs11] card.c:554:sc_select_file: returning with: 0
[opensc-pkcs11] card-cardos.c:751:cardos_set_security_env: returning with: 0
[opensc-pkcs11] framework-pkcs15.c:2124:pkcs15_prkey_sign: Sign complete. Result 128.
[opensc-pkcs11] pkcs11-object.c:554:C_Sign: Signing result was 0
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 1: CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:237:C_FindObjectsInit: C_FindObjectsInit(slot = 0)
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_CLASS = CKO_PUBLIC_KEY
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_ID = E75AF9392D491C6699CD2E2F12CC0CC9465726EA
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/3 matches
[opensc-pkcs11] pkcs11-object.c:307:C_FindObjectsInit: 1 matching objects
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_VALUE = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 3: CKA_VALUE = 308189028181008469765A7A6CFB6AD96CEE2EA15A85DBC7EA96595100AD91AC
OK
[opensc-pkcs11] pkcs11-object.c:237:C_FindObjectsInit: C_FindObjectsInit(slot = 0)
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_CLASS = CKO_PRIVATE_KEY
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/1 matches
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/4 matches
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/6 matches
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/8 matches
[opensc-pkcs11] pkcs11-object.c:307:C_FindObjectsInit: 4 matching objects
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 4: CKA_LABEL = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 4: CKA_LABEL = E03D0507-3CF4-49AE-BD66-F357C13FEC83
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 4: CKA_ID = <size inquiry>
[opensc-pkcs11] pkcs11-object.c:151:C_GetAttributeValue: Object 4: CKA_ID = 4B79A31A986F922C039E5149A84B63A8358D43CC
[opensc-pkcs11] pkcs11-object.c:237:C_FindObjectsInit: C_FindObjectsInit(slot = 0)
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_CLASS = CKO_PUBLIC_KEY
[opensc-pkcs11] pkcs11-object.c:238:C_FindObjectsInit: C_FindObjectsInit(): CKA_ID = 4B79A31A986F922C039E5149A84B63A8358D43CC
[opensc-pkcs11] pkcs11-object.c:296:C_FindObjectsInit: Object 0/5 matches
[opensc-pkcs11] pkcs11-object.c:307:C_FindObjectsInit: 1 matching objects
Segmentation fault

---

### Post by hezla on 2010-03-30
I have the same error on 9.10, it worked fine before the upgrade

---

