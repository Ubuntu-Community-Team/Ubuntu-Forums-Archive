---
title: "Cisco VPN Issues - Pulling Hair Out [long]"
date: 2012-06-11
forum: General Help
---

### Post by rhugga on 2012-06-11
I have now had this problem on Centos 5.x, 6.x, and all version of Ubuntu 11.x thru the current release.

I install the Cisco VPN client and IT WORKS FINE FOR A FEW DAYS. For example, I recently installed a Ubuntu 12 guest VM and was able to constantly disconnect and reconnect to my corporate VPN over a 4 day period w/o issues. 

Something happens that then breaks the VPN with the following information logged to syslog. I have searched and searched and searched for solutions to this to no avail.

Oddly, my unbuntu 10.x VM still chugging away. I connect to my company's VPN everyday and have been for 6 months. 

What breaks this on newer versions? I'm literally pulling my hair out. I've been using linux since kernel 0.97 and I've never dug in so deep and tried so hard to fix a problem and come up empty.

Here is what I see in syslog. I've searched and searched for just about every string in this output and has led nowhere: I hate being stuck at Ubuntu 10. (which has other unrelated problems)

From syslog: (kinda long)
------------------------------------------------------------------------------------------------------------------------
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: setCatalog File: i18n/MsgCatalog.cpp Line: 427 Invoked Function: setCatalog Return Code: -33554423 (0xFE000009) Description: GLOBAL_ERROR_UNEXPECTED Message translation catalog <AnyConnect> not in use.
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: ClientIfcBase File: ClientIfcBase.cpp Line: 134 Invoked Function: vpnapi Return Code: 0 (0x00000000) Description: vpnapi version 2.5.0217 () Initializing. 
Jun 11 07:47:19 ubuntu vpnui[2367]: Available preferences updated due to secure gateway configuration.
Jun 11 07:47:19 ubuntu vpnui[2367]: Current Preference Settings: CertificateStoreOverride: false CertificateStore: All ShowPreConnectMessage: false AutoConnectOnStart: true MinimizeOnConnect: true LocalLanAccess: false AutoReconnect: true AutoUpdate: true ProxySettings: Native PPPExclusion: Disable PPPExclusionServerIP:  EnableScripting: false TerminateScriptOnNextEvent: false 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: InitNSS File: Certificates/NSSCertUtils.cpp Line: 399 Invoked Function: getProfilePath Return Code: -31391739 (0xFE210005) Description: CERTSTORE_ERROR_NULL_POINTER 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: CNSSCertStore File: Certificates/NSSCertStore.cpp Line: 72 Invoked Function: CNSSCertUtils::InitNSS Return Code: -31391739 (0xFE210005) Description: CERTSTORE_ERROR_NULL_POINTER 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: addNSSStore File: Certificates/CollectiveCertStore.cpp Line: 999 Invoked Function: CNSSCertStore::CNSSCertStore Return Code: -31391739 (0xFE210005) Description: CERTSTORE_ERROR_NULL_POINTER 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: OpenStores File: Certificates/CollectiveCertStore.cpp Line: 248 Invoked Function: CCollectiveCertStore::addNSSStore Return Code: -31391739 (0xFE210005) Description: CERTSTORE_ERROR_NULL_POINTER 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: CvcGtkNotifyBalloon File: CvcGtkNotifyBalloon.cpp Line: 87 Invoked Function: dlopen Return Code: -33554427 (0xFE000005) Description: libnotify.so.1: cannot open shared object file: No such file or directory 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: OnNegotiateMessageTypesComplete File: ApiIpc.cpp Line: 534 Master Agent Connection started.
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: setStateInfo File: VPNStatsBase.cpp Line: 339 Invoked Function: CStateTlv::GetMUSHostAddr Return Code: -32374768 (0xFE120010) Description: TLV_ERROR_NO_ATTRIBUTE 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: processState File: ApiIpc.cpp Line: 1412 VPN state: Disconnected Network state: Network Accessible Network control state: Available Network type: Undefined
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: setState File: ClientIfcBase.cpp Line: 1224 Disconnected
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: attach File: ClientIfcBase.cpp Line: 424 Client successfully attached.
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: attach File: ClientIfcBase.cpp Line: 439 Event detection implemented in client program.
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: autoConnectIfEnabled File: ClientIfcBase.cpp Line: 555 Auto connect on start enabled.
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: getProfileNameFromHost File: ProfileMgr.cpp Line: 672 Invoked Function: getProfileNameFromHost Return Code: 0 (0x00000000) Description: No profile available for host myaccess.oraclevpn.com. 
Jun 11 07:47:19 ubuntu vpnui[2367]: Using default preferences. Some settings (e.g. certificate matching) may not function as expected if a local profile is expected to be used. Verify that the selected host is in the server list section of the profile and that the profile is configured on the secure gateway.
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: connect File: ClientIfcBase.cpp Line: 834 Connect requested
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: getProfileNameFromHost File: ProfileMgr.cpp Line: 672 Invoked Function: getProfileNameFromHost Return Code: 0 (0x00000000) Description: No profile available for host myaccess.oraclevpn.com. 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: getHostInitSettings File: ProfileMgr.cpp Line: 755 Profile "" not found. Using default settings
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: getProfileNameFromHost File: ProfileMgr.cpp Line: 672 Invoked Function: getProfileNameFromHost Return Code: 0 (0x00000000) Description: No profile available for host myaccess.oraclevpn.com. 
Jun 11 07:47:19 ubuntu vpnui[2367]: Using default preferences. Some settings (e.g. certificate matching) may not function as expected if a local profile is expected to be used. Verify that the selected host is in the server list section of the profile and that the profile is configured on the secure gateway.
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: getProfileNameFromHost File: ProfileMgr.cpp Line: 672 Invoked Function: getProfileNameFromHost Return Code: 0 (0x00000000) Description: No profile available for host myaccess.oraclevpn.com. 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: getHostInitSettings File: ProfileMgr.cpp Line: 755 Profile "" not found. Using default settings
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: enumerateCert File: Certificates/FileCertStore.cpp Line: 162 Invoked Function: enumerateCert Return Code: -31391730 (0xFE21000E) Description: CERTSTORE_ERROR_CERT_NOT_FOUND The /home/ccarson/.cisco/certificates/client/ directory was not found.
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: Enumerate File: Certificates/FileCertStore.cpp Line: 123 Invoked Function: Enumerate Return Code: -31391730 (0xFE21000E) Description: CERTSTORE_ERROR_CERT_NOT_FOUND 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: enumerateCert File: Certificates/FileCertStore.cpp Line: 162 Invoked Function: enumerateCert Return Code: -31391730 (0xFE21000E) Description: CERTSTORE_ERROR_CERT_NOT_FOUND The /opt/.cisco/certificates/client/ directory was not found.
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: Enumerate File: Certificates/FileCertStore.cpp Line: 123 Invoked Function: Enumerate Return Code: -31391730 (0xFE21000E) Description: CERTSTORE_ERROR_CERT_NOT_FOUND 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: getCertList File: ApiCert.cpp Line: 231 Invoked Function: ApiCert :: getCertList Return Code: 0 (0x00000000) Description: Number of certificates found: 0 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: getProfileNameFromHost File: ProfileMgr.cpp Line: 672 Invoked Function: getProfileNameFromHost Return Code: 0 (0x00000000) Description: No profile available for host myaccess.oraclevpn.com. 
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: getHostInitSettings File: ProfileMgr.cpp Line: 755 Profile "" not found. Using default settings
Jun 11 07:47:19 ubuntu vpnui[2367]: Function: initiateConnect File: ConnectMgr.cpp Line: 536 Initiating connection to: [https://myaccess.oraclevpn.com/](https://myaccess.oraclevpn.com/)
Jun 11 07:47:40 ubuntu vpnui[2367]: Function: SendRequest File: CTransportCurlStatic.cpp Line: 1467 Invoked Function: curl_easy_perform Return Code: -29949906 (0xFE37002E) Description: CTRANSPORT_ERROR_TIMEOUT error
Jun 11 07:47:40 ubuntu vpnui[2367]: Function: connect File: ConnectIfc.cpp Line: 334 Invoked Function: CTransport::SendRequest Return Code: -29949906 (0xFE37002E) Description: CTRANSPORT_ERROR_TIMEOUT 
Jun 11 07:47:40 ubuntu vpnui[2367]: Function: TranslateStatusCode File: ConnectIfc.cpp Line: 2375 Invoked Function: TranslateStatusCode Return Code: -29949906 (0xFE37002E) Description: CTRANSPORT_ERROR_TIMEOUT timeout
Jun 11 07:47:40 ubuntu vpnui[2367]: Function: doConnectIfcConnect File: ConnectMgr.cpp Line: 1178 Invoked Function: ConnectIfc::connect Return Code: -29949906 (0xFE37002E) Description: CTRANSPORT_ERROR_TIMEOUT 
Jun 11 07:47:40 ubuntu vpnui[2367]: Function: processIfcData File: ConnectMgr.cpp Line: 1449 Invoked Function: ConnectMgr :: processIfcData Return Code: -33554423 (0xFE000009) Description: GLOBAL_ERROR_UNEXPECTED Unrecognized content type (Unknown) received.
Jun 11 07:47:40 ubuntu vpnui[2367]: Function: processIfcData File: ConnectMgr.cpp Line: 1475 Unable to process response from myaccess.oraclevpn.com. 
Jun 11 07:47:40 ubuntu vpnui[2367]: Function: processIfcData File: ConnectMgr.cpp Line: 1564 Invoked Function: processIfcData Return Code: -33554423 (0xFE000009) Description: GLOBAL_ERROR_UNEXPECTED Unable to contact myaccess.oraclevpn.com. 
Jun 11 07:47:40 ubuntu vpnui[2367]: Function: initiateConnect File: ConnectMgr.cpp Line: 541 Connection failed.
Jun 11 07:47:40 ubuntu vpnui[2367]: Function: setState File: ClientIfcBase.cpp Line: 1224 Disconnected
Jun 11 07:47:40 ubuntu vpnui[2367]: Function: run File: ConnectMgr.cpp Line: 379 Invoked Function: ConnectMgr::initiateConnect Return Code: -29556727 (0xFE3D0009) Description: CONNECTMGR_ERROR_UNEXPECTED 
Jun 11 07:48:02 ubuntu dbus[395]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jun 11 07:48:03 ubuntu AptDaemon: INFO: Initializing daemon
Jun 11 07:48:04 ubuntu AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jun 11 07:48:04 ubuntu dbus[395]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jun 11 07:48:04 ubuntu AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jun 11 07:48:04 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/44df616139374fb6beee66023dd8f042
Jun 11 07:48:04 ubuntu AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/44df616139374fb6beee66023dd8f042
Jun 11 07:48:22 ubuntu AptDaemon.PackageKit: INFO: Get updates()
Jun 11 07:48:23 ubuntu AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/44df616139374fb6beee66023dd8f042
Jun 11 07:49:01 ubuntu vpnagent[839]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1657 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Jun 11 07:49:43  vpnagent[839]: last message repeated 2 times
Jun 11 07:51:21 ubuntu vpnagent[839]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1657 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Jun 11 07:51:51 ubuntu vpnagent[839]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1657 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Jun 11 07:54:04 ubuntu AptDaemon: INFO: Quitting due to inactivity
Jun 11 07:54:04 ubuntu AptDaemon: INFO: Quitting was requested
Jun 11 07:55:37 ubuntu vpnagent[839]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1657 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Jun 11 07:56:07 ubuntu vpnagent[839]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1657 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown
------------------------------------------------------------------------------------------------------------------------

Before today... syslog would be completely clean.

---

