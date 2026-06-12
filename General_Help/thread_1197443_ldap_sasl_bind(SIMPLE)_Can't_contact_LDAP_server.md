---
title: "ldap_sasl_bind(SIMPLE): Can't contact LDAP server"
date: 2009-06-26
forum: General Help
---

### Post by asmii on 2009-06-26
[COLOR=Blue]Hi All,

I have configured openldap on ubuntu 9.04.

In /etc/ldap/ldap.conf, if I provide "TLS_REQCERT allow", "ldapsearch -d5 -x" shows the result.

But if I changed it to "TLS_REQCERT demand", it just fails.

Reason is obvious I think. It has issues with security. With "Allow" option, it goes for a normal bind.

```
root@alcatel-ubuntu:/etc/ldap# ldapsearch -d5 -x
ldap_create
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP ldapagcf-alcatel-lucent.com:636
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 172.21.144.229:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
TLS: peer cert untrusted or revoked (0x42)
TLS: can't connect: (unknown error code).
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

```Can anyone please suggest me something so as to get rid of it.

Thanks in advance.

-Asmii
[/COLOR]

---

### Post by asmii on 2009-06-26
[COLOR=Blue]I followed the steps again defined in [https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)

During the following step, I saw some issues.

I created a ldif file namely enable-ca.ldif with following content.

[/COLOR][COLOR=Blue]```
dn: cn=config
add: olcTLSCACertificateFile
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem
-
add: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ssl/certs/server.crt
-
add: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ssl/private/server.key
```[/COLOR][COLOR=Blue]
Then I executed the command "ldapmodify -D "cn=admin,cn=config" -x -w 12345678 -f enable-ca.ldif"

I witnessed an error :

[/COLOR]```
modifying entry "cn=config"
ldap_modify: Inappropriate matching (18)
    additional info: modify/add: olcTLSCertificateFile: no equality matching rule
```[COLOR=Blue]

This is possibly the reason why ca is not enabled.

Can anyone please suggest me something about the error.

Thanks in advance.

-Asmii
[/COLOR]

---

### Post by asmii on 2009-06-26
Finally I am able to execute the ldif but after that slapd failed to start.

I wonder what may go wrong.

Please suggest.

-Asmii

---

### Post by lordharaldi on 2009-07-07
Hi!

I got the same problem.

Greetings,
lordharaldi

---

### Post by asmii on 2009-07-09
While restarting slapd, I see the following error :

```
main: TLS init def ctx failed: -1
```I am still in a fix what could be the problem.

-Asmii

---

### Post by asmii on 2009-07-09
[COLOR=Blue]After executing [/COLOR][COLOR=Blue]"ldapmodify -D "cn=admin,cn=config" -x -w 12345678 -f enable-ca.ldif", 3 lines are added to /etc/ldap/slapd.d/[/COLOR][COLOR=Blue]cn=config.ldif

[/COLOR]```
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem
olcTLSCertificateFile: /etc/ssl/certs/server.crt
olcTLSCertificateKeyFile: /etc/ssl/private/server.key
```[COLOR=Blue]

When I commented the last two lines like the following, [/COLOR] [COLOR=Blue]slapd started successfully.[/COLOR]
[COLOR=Blue] 
[/COLOR]```
olcTLSCACertificateFile: /etc/ssl/certs/cacert.pem
#olcTLSCertificateFile: /etc/ssl/certs/server.crt
#olcTLSCertificateKeyFile: /etc/ssl/private/server.key
```[COLOR=Blue]
[/COLOR]
[COLOR=Blue]But when I uncommented any one of the below 2 lines, it again started showing issues.

Please suggest.

-Asmii
[/COLOR]

---

### Post by meamens on 2009-07-13
I have the exact same problem! :(  Just playing with LDAP at the moment and this is my first server setup, so I have no clue what to try next.  Running in debug mode (sudo slapd -d 16383), it all seems fine until  it says "warning: cannot assess the validity of the ACL scope within backend naming context".  Here's the exact text :-

```

hdb_db_init: Initializing HDB database
>>> dnPrettyNormal: <dc=mycorp,dc=uk,dc=com>
=> ldap_bv2dn(dc=mycorp,dc=uk,dc=com,0)
<= ldap_bv2dn(dc=mycorp,dc=uk,dc=com)=0 
=> ldap_dn2bv(272)
<= ldap_dn2bv(dc=mycorp,dc=uk,dc=com)=0 
=> ldap_dn2bv(272)
<= ldap_dn2bv(dc=mycorp,dc=uk,dc=com)=0 
<<< dnPrettyNormal: <dc=mycorp,dc=uk,dc=com>, <dc=mycorp,dc=uk,dc=com>
>>> dnNormalize: <cn=admin,dc=mycorp,dc=uk,dc=com>
=> ldap_bv2dn(cn=admin,dc=mycorp,dc=uk,dc=com,0)
<= ldap_bv2dn(cn=admin,dc=mycorp,dc=uk,dc=com)=0 
=> ldap_dn2bv(272)
<= ldap_dn2bv(cn=admin,dc=mycorp,dc=uk,dc=com)=0 
<<< dnNormalize: <cn=admin,dc=mycorp,dc=uk,dc=com>
Backend ACL: access to attrs=userPassword,shadowLastChange
	by dn.base="cn=admin,dc=mycorp,dc=uk,dc=com" write
	by anonymous auth
	by self write
	by * none

/etc/ldap/slapd.d: line 1: warning: cannot assess the validity of the ACL scope within backend naming context
>>> dnNormalize: <>
<<< dnNormalize: <>
Backend ACL: access to dn.base=""
	by * read

/etc/ldap/slapd.d: line 1: warning: ACL appears to be out of scope within backend naming context
>>> dnNormalize: <cn=admin,dc=mycorp,dc=uk,dc=com>
=> ldap_bv2dn(cn=admin,dc=mycorp,dc=uk,dc=com,0)
<= ldap_bv2dn(cn=admin,dc=mycorp,dc=uk,dc=com)=0 
=> ldap_dn2bv(272)
<= ldap_dn2bv(cn=admin,dc=mycorp,dc=uk,dc=com)=0 
<<< dnNormalize: <cn=admin,dc=mycorp,dc=uk,dc=com>
Backend ACL: access to *
	by dn.base="cn=admin,dc=mycorp,dc=uk,dc=com" write
	by * read

/etc/ldap/slapd.d: line 1: warning: cannot assess the validity of the ACL scope within backend naming context
index objectClass 0x0004
index entryUUID 0x0004
index uid 0x0716
send_ldap_result: conn=-1 op=0 p=0
send_ldap_result: err=0 matched="" text=""
>>> dnNormalize: <cn=Subschema>
=> ldap_bv2dn(cn=Subschema,0)
<= ldap_bv2dn(cn=Subschema)=0 
=> ldap_dn2bv(272)
<= ldap_dn2bv(cn=subschema)=0 
<<< dnNormalize: <cn=subschema>
matching_rule_use_init
    1.2.840.113556.1.4.804 (integerBitOrMatch): matchingRuleUse: ( 1.2.840.113556.1.4.804 NAME 'integerBitOrMatch' APPLIES ( supportedLDAPVersion $ entryTtl $ uidNumber $ gidNumber $ olcConcurrency $ olcConnMaxPending $ olcConnMaxPendingAuth $ olcIdleTimeout $ olcIndexSubstrIfMinLen $ olcIndexSubstrIfMaxLen $ olcIndexSubstrAnyLen $ olcIndexSubstrAnyStep $ olcIndexIntLen $ olcLocalSSF $ olcMaxDerefDepth $ olcReplicationInterval $ olcSockbufMaxIncoming $ olcSockbufMaxIncomingAuth $ olcThreads $ olcToolThreads $ olcDbCacheFree $ olcDbCacheSize $ olcDbDNcacheSize $ olcDbIDLcacheSize $ olcDbSearchStack $ olcDbShmKey $ mailPreferenceOption $ shadowLastChange $ shadowMin $ shadowMax $ shadowWarning $ shadowInactive $ shadowExpire $ shadowFlag $ ipServicePort $ ipProtocolNumber $ oncRpcNumber ) )
    1.2.840.113556.1.4.803 (integerBitAndMatch): matchingRuleUse: ( 1.2.840.113556.1.4.803 NAME 'integerBitAndMatch' APPLIES ( supportedLDAPVersion $ entryTtl $ uidNumber $ gidNumber $ olcConcurrency $ olcConnMaxPending $ olcConnMaxPendingAuth $ olcIdleTimeout $ olcIndexSubstrIfMinLen $ olcIndexSubstrIfMaxLen $ olcIndexSubstrAnyLen $ olcIndexSubstrAnyStep $ olcIndexIntLen $ olcLocalSSF $ olcMaxDerefDepth $ olcReplicationInterval $ olcSockbufMaxIncoming $ olcSockbufMaxIncomingAuth $ olcThreads $ olcToolThreads $ olcDbCacheFree $ olcDbCacheSize $ olcDbDNcacheSize $ olcDbIDLcacheSize $ olcDbSearchStack $ olcDbShmKey $ mailPreferenceOption $ shadowLastChange $ shadowMin $ shadowMax $ shadowWarning $ shadowInactive $ shadowExpire $ shadowFlag $ ipServicePort $ ipProtocolNumber $ oncRpcNumber ) )
    1.3.6.1.4.1.1466.109.114.2 (caseIgnoreIA5Match): matchingRuleUse: ( 1.3.6.1.4.1.1466.109.114.2 NAME 'caseIgnoreIA5Match' APPLIES ( altServer $ olcDbConfig $ mail $ dc $ associatedDomain $ email $ aRecord $ mDRecord $ mXRecord $ nSRecord $ sOARecord $ cNAMERecord $ janetMailbox $ gecos $ homeDirectory $ loginShell $ memberUid $ memberNisNetgroup $ ipHostNumber $ ipNetworkNumber $ ipNetmaskNumber $ macAddress $ bootFile $ nisMapEntry $ mailLocalAddress $ mailHost $ mailRoutingAddress $ rfc822MailMember ) )
    1.3.6.1.4.1.1466.109.114.1 (caseExactIA5Match): matchingRuleUse: ( 1.3.6.1.4.1.1466.109.114.1 NAME 'caseExactIA5Match' APPLIES ( altServer $ olcDbConfig $ mail $ dc $ associatedDomain $ email $ aRecord $ mDRecord $ mXRecord $ nSRecord $ sOARecord $ cNAMERecord $ janetMailbox $ gecos $ homeDirectory $ loginShell $ memberUid $ memberNisNetgroup $ ipHostNumber $ ipNetworkNumber $ ipNetmaskNumber $ macAddress $ bootFile $ nisMapEntry $ mailLocalAddress $ mailHost $ mailRoutingAddress $ rfc822MailMember ) )
    2.5.13.39 (certificateListMatch):     2.5.13.38 (certificateListExactMatch): matchingRuleUse: ( 2.5.13.38 NAME 'certificateListExactMatch' APPLIES ( authorityRevocationList $ certificateRevocationList $ deltaRevocationList ) )
    2.5.13.35 (certificateMatch):     2.5.13.34 (certificateExactMatch): matchingRuleUse: ( 2.5.13.34 NAME 'certificateExactMatch' APPLIES ( userCertificate $ cACertificate ) )
    2.5.13.30 (objectIdentifierFirstComponentMatch): matchingRuleUse: ( 2.5.13.30 NAME 'objectIdentifierFirstComponentMatch' APPLIES ( supportedControl $ supportedExtension $ supportedFeatures $ ldapSyntaxes $ supportedApplicationContext ) )
    2.5.13.29 (integerFirstComponentMatch): matchingRuleUse: ( 2.5.13.29 NAME 'integerFirstComponentMatch' APPLIES ( supportedLDAPVersion $ entryTtl $ uidNumber $ gidNumber $ olcConcurrency $ olcConnMaxPending $ olcConnMaxPendingAuth $ olcIdleTimeout $ olcIndexSubstrIfMinLen $ olcIndexSubstrIfMaxLen $ olcIndexSubstrAnyLen $ olcIndexSubstrAnyStep $ olcIndexIntLen $ olcLocalSSF $ olcMaxDerefDepth $ olcReplicationInterval $ olcSockbufMaxIncoming $ olcSockbufMaxIncomingAuth $ olcThreads $ olcToolThreads $ olcDbCacheFree $ olcDbCacheSize $ olcDbDNcacheSize $ olcDbIDLcacheSize $ olcDbSearchStack $ olcDbShmKey $ mailPreferenceOption $ shadowLastChange $ shadowMin $ shadowMax $ shadowWarning $ shadowInactive $ shadowExpire $ shadowFlag $ ipServicePort $ ipProtocolNumber $ oncRpcNumber ) )
    2.5.13.27 (generalizedTimeMatch): matchingRuleUse: ( 2.5.13.27 NAME 'generalizedTimeMatch' APPLIES ( createTimestamp $ modifyTimestamp ) )
    2.5.13.24 (protocolInformationMatch): matchingRuleUse: ( 2.5.13.24 NAME 'protocolInformationMatch' APPLIES protocolInformation )
    2.5.13.23 (uniqueMemberMatch): matchingRuleUse: ( 2.5.13.23 NAME 'uniqueMemberMatch' APPLIES uniqueMember )
    2.5.13.22 (presentationAddressMatch): matchingRuleUse: ( 2.5.13.22 NAME 'presentationAddressMatch' APPLIES presentationAddress )
    2.5.13.20 (telephoneNumberMatch): matchingRuleUse: ( 2.5.13.20 NAME 'telephoneNumberMatch' APPLIES ( telephoneNumber $ homePhone $ mobile $ pager ) )
    2.5.13.17 (octetStringMatch): matchingRuleUse: ( 2.5.13.17 NAME 'octetStringMatch' APPLIES ( userPassword $ olcDbCryptKey ) )
    2.5.13.16 (bitStringMatch): matchingRuleUse: ( 2.5.13.16 NAME 'bitStringMatch' APPLIES x500UniqueIdentifier )
    2.5.13.14 (integerMatch): matchingRuleUse: ( 2.5.13.14 NAME 'integerMatch' APPLIES ( supportedLDAPVersion $ entryTtl $ uidNumber $ gidNumber $ olcConcurrency $ olcConnMaxPending $ olcConnMaxPendingAuth $ olcIdleTimeout $ olcIndexSubstrIfMinLen $ olcIndexSubstrIfMaxLen $ olcIndexSubstrAnyLen $ olcIndexSubstrAnyStep $ olcIndexIntLen $ olcLocalSSF $ olcMaxDerefDepth $ olcReplicationInterval $ olcSockbufMaxIncoming $ olcSockbufMaxIncomingAuth $ olcThreads $ olcToolThreads $ olcDbCacheFree $ olcDbCacheSize $ olcDbDNcacheSize $ olcDbIDLcacheSize $ olcDbSearchStack $ olcDbShmKey $ mailPreferenceOption $ shadowLastChange $ shadowMin $ shadowMax $ shadowWarning $ shadowInactive $ shadowExpire $ shadowFlag $ ipServicePort $ ipProtocolNumber $ oncRpcNumber ) )
    2.5.13.13 (booleanMatch): matchingRuleUse: ( 2.5.13.13 NAME 'booleanMatch' APPLIES ( hasSubordinates $ olcAddContentAcl $ olcGentleHUP $ olcHidden $ olcLastMod $ olcMirrorMode $ olcMonitoring $ olcReadOnly $ olcReverseLookup $ olcDbChecksum $ olcDbNoSync $ olcDbDirtyRead $ olcDbLinearIndex ) )
    2.5.13.11 (caseIgnoreListMatch): matchingRuleUse: ( 2.5.13.11 NAME 'caseIgnoreListMatch' APPLIES ( postalAddress $ registeredAddress $ homePostalAddress ) )
    2.5.13.8 (numericStringMatch): matchingRuleUse: ( 2.5.13.8 NAME 'numericStringMatch' APPLIES ( x121Address $ internationaliSDNNumber ) )
    2.5.13.7 (caseExactSubstringsMatch): matchingRuleUse: ( 2.5.13.7 NAME 'caseExactSubstringsMatch' APPLIES ( serialNumber $ destinationIndicator $ dnQualifier ) )
    2.5.13.6 (caseExactOrderingMatch): matchingRuleUse: ( 2.5.13.6 NAME 'caseExactOrderingMatch' APPLIES ( serialNumber $ destinationIndicator $ dnQualifier ) )
    2.5.13.5 (caseExactMatch): matchingRuleUse: ( 2.5.13.5 NAME 'caseExactMatch' APPLIES ( supportedSASLMechanisms $ vendorName $ vendorVersion $ ref $ name $ cn $ uid $ labeledURI $ description $ olcConfigFile $ olcConfigDir $ olcAccess $ olcAllows $ olcArgsFile $ olcAttributeOptions $ olcAttributeTypes $ olcAuthIDRewrite $ olcAuthzPolicy $ olcAuthzRegexp $ olcBackend $ olcDatabase $ olcDisallows $ olcDitContentRules $ olcInclude $ olcLdapSyntaxes $ olcLimits $ olcLogFile $ olcLogLevel $ olcModuleLoad $ olcModulePath $ olcObjectClasses $ olcObjectIdentifier $ olcOverlay $ olcPasswordCryptSaltFormat $ olcPasswordHash $ olcPidFile $ olcPlugin $ olcPluginLogFile $ olcReferral $ olcReplica $ olcReplicaArgsFile $ olcReplicaPidFile $ olcReplogFile $ olcRequires $ olcRestrict $ olcRootDSE $ olcRootPW $ olcSaslHost $ olcSaslRealm $ olcSaslSecProps $ olcSecurity $ olcServerID $ olcSizeLimit $ olcSortVals $ olcSubordinate $ olcSyncrepl $ olcTimeLimit $ olcTLSCACertificateFile $ olcTLSCACertificatePath $ olcTLSCertificateFile $ olcTLSCertificateKeyFile $ olcTLSCipherSuite $ olcTLSCRLCheck $ olcTLSCRLFile $ olcTLSRandFile $ olcTLSVerifyClient $ olcTLSDHParamFile $ olcTLSProtocolMin $ olcUpdateRef $ olcDbDirectory $ olcDbCheckpoint $ olcDbCryptFile $ olcDbPageSize $ olcDbIndex $ olcDbLockDetect $ olcDbMode $ knowledgeInformation $ sn $ serialNumber $ c $ l $ st $ street $ o $ ou $ title $ businessCategory $ postalCode $ postOfficeBox $ physicalDeliveryOfficeName $ destinationIndicator $ givenName $ initials $ generationQualifier $ dnQualifier $ houseIdentifier $ dmdName $ pseudonym $ textEncodedORAddress $ info $ drink $ roomNumber $ userClass $ host $ documentIdentifier $ documentTitle $ documentVersion $ documentLocation $ personalTitle $ co $ uniqueIdentifier $ organizationalStatus $ buildingName $ documentPublisher $ ipServiceProtocol $ nisMapName $ carLicense $ departmentNumber $ displayName $ employeeNumber $ employeeType $ preferredLanguage ) )
    2.5.13.4 (caseIgnoreSubstringsMatch): matchingRuleUse: ( 2.5.13.4 NAME 'caseIgnoreSubstringsMatch' APPLIES ( serialNumber $ destinationIndicator $ dnQualifier ) )
    2.5.13.3 (caseIgnoreOrderingMatch): matchingRuleUse: ( 2.5.13.3 NAME 'caseIgnoreOrderingMatch' APPLIES ( serialNumber $ destinationIndicator $ dnQualifier ) )
    2.5.13.2 (caseIgnoreMatch): matchingRuleUse: ( 2.5.13.2 NAME 'caseIgnoreMatch' APPLIES ( supportedSASLMechanisms $ vendorName $ vendorVersion $ ref $ name $ cn $ uid $ labeledURI $ description $ olcConfigFile $ olcConfigDir $ olcAccess $ olcAllows $ olcArgsFile $ olcAttributeOptions $ olcAttributeTypes $ olcAuthIDRewrite $ olcAuthzPolicy $ olcAuthzRegexp $ olcBackend $ olcDatabase $ olcDisallows $ olcDitContentRules $ olcInclude $ olcLdapSyntaxes $ olcLimits $ olcLogFile $ olcLogLevel $ olcModuleLoad $ olcModulePath $ olcObjectClasses $ olcObjectIdentifier $ olcOverlay $ olcPasswordCryptSaltFormat $ olcPasswordHash $ olcPidFile $ olcPlugin $ olcPluginLogFile $ olcReferral $ olcReplica $ olcReplicaArgsFile $ olcReplicaPidFile $ olcReplogFile $ olcRequires $ olcRestrict $ olcRootDSE $ olcRootPW $ olcSaslHost $ olcSaslRealm $ olcSaslSecProps $ olcSecurity $ olcServerID $ olcSizeLimit $ olcSortVals $ olcSubordinate $ olcSyncrepl $ olcTimeLimit $ olcTLSCACertificateFile $ olcTLSCACertificatePath $ olcTLSCertificateFile $ olcTLSCertificateKeyFile $ olcTLSCipherSuite $ olcTLSCRLCheck $ olcTLSCRLFile $ olcTLSRandFile $ olcTLSVerifyClient $ olcTLSDHParamFile $ olcTLSProtocolMin $ olcUpdateRef $ olcDbDirectory $ olcDbCheckpoint $ olcDbCryptFile $ olcDbPageSize $ olcDbIndex $ olcDbLockDetect $ olcDbMode $ knowledgeInformation $ sn $ serialNumber $ c $ l $ st $ street $ o $ ou $ title $ businessCategory $ postalCode $ postOfficeBox $ physicalDeliveryOfficeName $ destinationIndicator $ givenName $ initials $ generationQualifier $ dnQualifier $ houseIdentifier $ dmdName $ pseudonym $ textEncodedORAddress $ info $ drink $ roomNumber $ userClass $ host $ documentIdentifier $ documentTitle $ documentVersion $ documentLocation $ personalTitle $ co $ uniqueIdentifier $ organizationalStatus $ buildingName $ documentPublisher $ ipServiceProtocol $ nisMapName $ carLicense $ departmentNumber $ displayName $ employeeNumber $ employeeType $ preferredLanguage ) )
    1.2.36.79672281.1.13.3 (rdnMatch):     2.5.13.1 (distinguishedNameMatch): matchingRuleUse: ( 2.5.13.1 NAME 'distinguishedNameMatch' APPLIES ( creatorsName $ modifiersName $ subschemaSubentry $ entryDN $ namingContexts $ aliasedObjectName $ dynamicSubtrees $ distinguishedName $ seeAlso $ olcDefaultSearchBase $ olcRootDN $ olcSchemaDN $ olcSuffix $ olcUpdateDN $ member $ owner $ roleOccupant $ manager $ documentAuthor $ secretary $ associatedName $ dITRedirect ) )
    2.5.13.0 (objectIdentifierMatch): matchingRuleUse: ( 2.5.13.0 NAME 'objectIdentifierMatch' APPLIES ( supportedControl $ supportedExtension $ supportedFeatures $ supportedApplicationContext ) )
main: TLS init def ctx failed: -1

```

I hope this means something to someone as I'd love to get this working!  So has anyone else got any ideas??

Cheers,
Marc

---

### Post by asmii on 2009-07-15
[COLOR=Blue]Hi,

Try using certtools to create key and certificate files instead of the existing procedures defined.

This solved my problem and I hope this works for others too.

However this solves the certificate and key issue due to which slapd shows error when restarted. This doesn't solve the issue defined in my first post. I am able to get rid of the error and slapd now starts successfully, "[/COLOR]  [COLOR=Blue]TLS_REQCERT demand" still creates issues for me. It only works with "[/COLOR][COLOR=Blue]TLS_REQCERT allow".

-Asmii[/COLOR]

---

### Post by carlos@idfx on 2011-02-09
Quote:
 	 	 		 			 				 					Originally Posted by **luvshines** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10432448#post10432448") 				
 				[I]Though I haven't seen that error,  but following post has some troubleshooting tips in comment #6
[http://ubuntuforums.org/showthread.php?p=8154148](http://ubuntuforums.org/showthread.php?p=8154148)
See if that helps[/I]

Ok, so I've gone back and "purged" slapd and re-installed it.

Then following the tutorial referenced in the above post, done  everything it states, simply copying and pasting the required code into  the shell and running it and creating docs with the specified text as  stipulated.

Without modifying any of the variables to personalize the database to  meet my domain requirements I succeeded in getting all the way to the  final step which is querying the database.

What follows is my result.

 	Code:
 	idfxadmin@maverick01:~$ ldapsearch -x -H ldap://admin.home.local -b dc=home,dc=local
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1) 
The one thing I changed after cutting and pasting this into my  shell was I inserted "admin.home.local" where it had said  "dustball.home.local"

I have migrated this thread from:
[[IMG]http://ubuntuforums.org/images/misc/navbits_start.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10444028#") 				  				[Ubuntu Forums]("http://ubuntuforums.org/index.php")   	> [The Ubuntu Forum  Community]("http://ubuntuforums.org/forumdisplay.php?f=130")   	> [Main Support  Categories]("http://ubuntuforums.org/forumdisplay.php?f=327")   	> [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339")   			 			 				[[IMG]http://ubuntuforums.org/images/misc/navbits_finallink_ltr.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10444028") ** 	[COLOR=#D15600][B][xubuntu]**[/COLOR]  OpenLdap Install/Config  [/B]
to:
[[IMG]http://ubuntuforums.org/images/misc/navbits_start.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=1197443#") 				  				[Ubuntu Forums]("http://ubuntuforums.org/index.php")   	> [The  Ubuntu Forum  Community]("http://ubuntuforums.org/forumdisplay.php?f=130")   	> [Main  Support  Categories]("http://ubuntuforums.org/forumdisplay.php?f=327")   	> [General  Help]("http://ubuntuforums.org/forumdisplay.php?f=331")   			 			 				[[IMG]http://ubuntuforums.org/images/misc/navbits_finallink_ltr.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=1197443") ** 	[COLOR=#980101][B][ubuntu]**[/COLOR]   ldap_sasl_bind(SIMPLE): Can't contact LDAP server  [/B]

If you  have found my post here and can help, please submit your replies here.

Thank you all in advance for your dedication to the community and remember, I love  your work!

---

### Post by luvshines on 2011-02-09
@Carlos

Is the LDAP port reachable from client machine ??```

# Assuming you didn't change the default 389 port
nc -zv <ldap-server-ip> 389
```

Also try it using the name admin.home.local since you are using that in LDAP URI

---

### Post by carlos@idfx on 2011-02-10
@ Luvshines
Ok, don't laugh, I just realized last night after I was going over the  OpenLdap official install page that I had blindly forgotten/failed to  install:
Cyrus SASL
Kerberos
Berkeley DB

So now with those items in place I begin my journey anew. Certainly to  face new challenges and many more blind corners.

By the way, the server is pingable and port 389 is listed properly in  /etc/services.

I assume that since you're advising me you have successfully deployed  OpenLdap in the past? Was it as difficult as it seems?

Thanks for following my evolution.

---

### Post by luvshines on 2011-02-10
> **carlos@idfx said:**
> @ Luvshines
Ok, don't laugh, I just realized last night after I was going over the  OpenLdap official install page that I had blindly forgotten/failed to  install:
Cyrus SASL
Kerberos
Berkeley DB

So now with those items in place I begin my journey anew. Certainly to  face new challenges and many more blind corners.

But do you actually need kerberos and SASL ??
I don't think they are required for a basic LDAP server setup.
Infact kerberos would be altogether a different authentication mechanism (which can be used along with LDAP if one intends)

As for the db backend for LDAP, yeah you would need one. And there are loads of them which can be used(man slapd.conf)
I have been using bdb(berkeley db) as backend for my LDAP server configurations
> I assume that since you're advising me you have successfully deployed  OpenLdap in the past? Was it as difficult as it seems?

Yes, I have deploying LDAP for the past 2 yrs , it's part of my job :)
But I have been doing it on RHEL with the old mechanism of slapd.conf . That setup is really easy and takes just 2-3 min in setting up LDAP server (yeah, believe me max 5 minutes)
I have seen ppl struggling here with the new methods of slapd.d, but I haven't tried that
Even on my Ubuntu machine, I used my older and well versed method of using slapd.conf file

For your case, use -d5 (or higher debug level) with ldapsearch command. That can give better insight of what the issue could be

---

### Post by mdixon@teemco on 2011-05-23
I've been working through these same issues with openldap. The solution to this particular problem that worked for me was in my ldap.conf file setup.

BASE   dc=example,dc=com
**URI      ldap://server-ip/**

SIZELIMIT     0
TIMELIMIT     0
DEREF           never

TLS_REQCERT allow

Hope this helps.

---

### Post by rahuljanghel on 2013-03-19
Hi Folk,

I got error "ldap_sasl_bind(simple) can't contact ldap server (-1)" when i was trying LDAP with "https://help.ubuntu.com/12.04/serverguide/openldap-server.html"

I did some searching, but finally got resolved when i UN-commnet below lines from /etc/hosts
127.0.0.1       localhost

Strange, but worked for me. :-)

Regards,
Rahul Janghel.

---

