---
title: "Integrate Ubuntu 10.10 in the Domain of the Active Directory"
date: 2011-02-10
forum: General Help
---

### Post by suporte.neus on 2011-02-10
Good Morning, 
  I’m trying to integrate the Ubuntu 10.10 in the domain of the Active  Directory, and run the command: domainjoin-cli --loglevel verbose join  dominio.com.br administrador 
  I get this error: 
  Segmentation fault 
Joining to AD Domain:   dominio.com.br 
With Computer DNS Name: testead.dominio.com.br 
  [EMAIL="administrador@DOMINIO.COM.BR"]administrador@DOMINIO.COM.BR[/EMAIL]’s password: 
[2011/02/09 08:40:44,  5] lib/debug.c:debug_dump_status(395) 
  INFO: Current debug levels: 
    all: True/10 
    tdb: False/0 
    printdrivers: False/0 
    lanman: False/0 
    smb: False/0 
    rpc_parse: False/0 
    rpc_srv: False/0 
    rpc_cli: False/0 
    passdb: False/0 
    sam: False/0 
    auth: False/0 
    winbind: False/0 
    vfs: False/0 
    idmap: False/0 
    quota: False/0 
    acls: False/0 
    locking: False/0 
    msdfs: False/0 
    dmapi: False/0 
    registry: False/0 
[2011/02/09 08:40:44,  3] param/loadparm.c:lp_load(5688) 
  lp_load: refreshing parameters 
[2011/02/09 08:40:44,  3] param/loadparm.c:init_globals(1477) 
  Initialising global parameters 
[2011/02/09 08:40:44,  3] param/params.c:pm_process(569) 
  params.c:pm_process() - Processing configuration file “/tmp/centeristmpKDz9To/etc/samba/lwiauthd.conf” 
[2011/02/09 08:40:44,  3] param/loadparm.c:do_section(4384) 
  Processing section “[global]” 
  doing parameter workgroup = WORKGROUP 
  doing parameter security = ads 
  doing parameter passdb backend = tdbsam 
  doing parameter disable netbios = yes 
  doing parameter idmap domains = default 
  doing parameter idmap config default:default = yes 
  doing parameter idmap config default:backend = lwopen 
  doing parameter idmap config default:readonly = yes 
  doing parameter idmap alloc backend = tdb 
  doing parameter idmap alloc config:range = 9000 - 9999 
  doing parameter idmap cache time = 3600 
  doing parameter idmap negative cache time = 300 
  doing parameter winbind cache time = 900 
  doing parameter winbind offline logon = yes 
  doing parameter winbind refresh tickets = yes 
  doing parameter winbind replacement character = ^ 
  doing parameter winbind normalize names = yes 
  doing parameter winbind expand groups = 10 
  doing parameter template shell = /bin/bash 
  doing parameter template homedir = /home/%D/%U 
  doing parameter machine password timeout = 2592000 
  doing parameter realm = DOMINIO.COM.BR 
  doing parameter use kerberos keytab = yes 
[2011/02/09 08:40:44,  4] param/loadparm.c:lp_load(5730) 
  pm_process() returned Yes 
[2011/02/09 08:40:44,  7] param/loadparm.c:lp_servicenumber(5892) 
  lp_servicenumber: couldn’t find homes 
[2011/02/09 08:40:44, 10] param/loadparm.c:set_server_role(4934) 
  set_server_role: role = ROLE_DOMAIN_MEMBER 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(104) 
  Attempting to register new charset UCS-2LE 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(112) 
  Registered charset UCS-2LE 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(104) 
  Attempting to register new charset UTF-16LE 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(112) 
  Registered charset UTF-16LE 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(104) 
  Attempting to register new charset UCS-2BE 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(112) 
  Registered charset UCS-2BE 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(104) 
  Attempting to register new charset UTF-16BE 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(112) 
  Registered charset UTF-16BE 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(104) 
  Attempting to register new charset UTF8 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(112) 
  Registered charset UTF8 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(104) 
  Attempting to register new charset UTF-8 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(112) 
  Registered charset UTF-8 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(104) 
  Attempting to register new charset ASCII 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(112) 
  Registered charset ASCII 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(104) 
  Attempting to register new charset 646 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(112) 
  Registered charset 646 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(104) 
  Attempting to register new charset ISO-8859-1 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(112) 
  Registered charset ISO-8859-1 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(104) 
  Attempting to register new charset UCS2-HEX 
[2011/02/09 08:40:44,  5] lib/iconv.c:smb_register_charset(112) 
  Registered charset UCS2-HEX 
[2011/02/09 08:40:44,  2] lib/util_file.c:map_file(239) 
  map_file: Failed to load /usr/lib/likewise-open/valid.dat - No such file or directory 
[2011/02/09 08:40:44,  2] lib/util_unistr.c:init_valid_table(203) 
  creating default valid table 
[2011/02/09 08:40:44,  5] lib/util.c:init_names(274) 
  Netbios name list:- 
  my_netbios_names[0]="TESTEAD" 
[2011/02/09 08:40:44,  2] lib/interface.c:add_interface(343) 
  added interface eth0 ip=192.168.0.57 bcast=192.168.0.255 netmask=255.255.255.0 
[2011/02/09 08:40:44,  5] lib/gencache.c:gencache_init(61) 
  Opening cache file at /var/lib/likewise-open/gencache.tdb 
[2011/02/09 08:40:44, 10] lib/gencache.c:gencache_get(194) 
  Cache entry with key = AD_SITENAME/DOMAIN/DOMINIO.COM.BR couldn’t be found 
[2011/02/09 08:40:44,  5] libads/dns.c:sitename_fetch(834) 
  sitename_fetch: No stored sitename for DOMINIO.COM.BR 
[2011/02/09 08:40:44,  4] libsmb/namequery_dc.c:ads_dc_name(73) 
  ads_dc_name: domain=WORKGROUP 
[2011/02/09 08:40:44, 10] lib/gencache.c:gencache_get(194) 
  Cache entry with key = AD_SITENAME/DOMAIN/DOMINIO.COM.BR couldn’t be found 
[2011/02/09 08:40:44,  5] libads/dns.c:sitename_fetch(834) 
  sitename_fetch: No stored sitename for DOMINIO.COM.BR 
[2011/02/09 08:40:44,  6] libads/ldap.c:ads_find_dc(309) 

[2011/02/09 08:40:44,  6] libads/ldap.c:ads_find_dc(309) 
  ads_find_dc: looking for realm ‘DOMINIO.COM.BR’ 
[2011/02/09 08:40:44,  8] libsmb/namequery.c:get_sorted_dc_list(2089) 
  get_sorted_dc_list: attempting lookup for name DOMINIO.COM.BR (sitename NULL) using [ads] 
[2011/02/09 08:40:44, 10] lib/gencache.c:gencache_get(194) 
  Cache entry with key = SAF/DOMAIN/DOMINIO.COM.BR couldn’t be found 
[2011/02/09 08:40:44,  5] libsmb/namequery.c:saf_fetch(135) 
  saf_fetch: failed to find server for “DOMINIO.COM.BR” domain 
[2011/02/09 08:40:44,  3] libsmb/namequery.c:get_dc_list(1910) 
  get_dc_list: preferred server list: “, *” 
[2011/02/09 08:40:44, 10] libsmb/namequery.c:internal_resolve_name(1447) 
  internal_resolve_name: looking up DOMINIO.COM.BR#1c (sitename (null)) 
[2011/02/09 08:40:44, 10] lib/gencache.c:gencache_get(194) 
  Cache entry with key = NBT/DOMINIO.COM.BR#1C couldn’t be found 
[2011/02/09 08:40:44,  5] libsmb/namecache.c:namecache_fetch(229) 
  no entry for DOMINIO.COM.BR#1C found. 
[2011/02/09 08:40:44,  5] libsmb/namequery.c:resolve_ads(1341) 
  resolve_ads: Attempting to resolve DCs for DOMINIO.COM.BR using DNS 
[2011/02/09 08:40:44,  3] libads/dns.c:dns_send_req(363) 
  ads_dns_lookup_srv: Failed to resolve _ldap._tcp.dc._msdcs.DOMINIO.COM.BR (Success) 
[2011/02/09 08:40:44,  3] libads/dns.c:ads_dns_lookup_srv(433) 
  ads_dns_lookup_srv: Failed to send DNS query (NT_STATUS_UNSUCCESSFUL) 
[2011/02/09 08:40:44,  8] libsmb/namequery.c:get_dc_list(1931) 
  Adding 0 DC’s from auto lookup 
[2011/02/09 08:40:44,  4] libsmb/namequery.c:get_dc_list(1942) 
  get_dc_list: no servers found 
[2011/02/09 08:40:44,  0] utils/net_ads.c:ads_startup_int(493) 
  ads_connect: No logon servers 
[2011/02/09 08:40:44, 10] intl/lang_tdb.c:lang_tdb_init(134) 
  lang_tdb_init: /usr/lib/likewise-open/pt_BR:pt:en.msg: No such file or directory 
Failed to contact DC when trying to synchronize local system clock! 
None of the domain controllers listed in DNS could be contacted, or there are no DCs listed in DNS. 
[2011/02/09 08:40:44,  2] utils/net.c:main(1178) 
  return code = -1 
  Error: Unable to join domain [code 0x0008000e] 
  Domain join operation failed to create the computer account in Active  Directory. Common causes are a bad administrator password, a bad OU  name, or an existing computer account without modification 
permissions. 
  ---------------------------------------------------------------------------------------------- 
  Obs 1: The user “administrador” is the superuser of the server. 
Obs 2: The time at the client (testead) is already sincronized with the server. 
   Here are some configuration files: 
  ------------------------------------------------------------------------------------- 
smb.conf 
  [global] 
          security = ads 
        realm = DOMINIO.COM.BR 
        password server = testead 
# note that workgroup is the ‘short’ domain name 
        workgroup = DOMINIO.COM.BR 
#       winbind separator = + 
        idmap uid = 10000-20000 
        idmap gid = 10000-20000 
        winbind enum users = yes 
        winbind enum groups = yes 
        winbind use default domain = yes 
        template homedir = /home/%D/%U 
        template shell = /bin/bash 
        client use spnego = yes 
        client ntlmv2 auth = yes 
        encrypt passwords = yes 
        winbind use default domain = yes 
        restrict anonymous = 2 
      interfaces = 127.0.0.1 eth0 
    bind interfaces only = true 
    server string = 
  -------------------------------------------------------------------------------------------- 
  krb5.conf 
  [libdefaults] 
        krb4_config = /etc/krb.conf 
        krb4_realms = /etc/krb.realms 
        kdc_timesync = 1 
        ccache_type = 4 
        forwardable = true 
        ticket_lifetime = 24000 
        default_realm = DOMINIO.COM.BR 
        default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc 
        default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc 
        proxiable = true 
        v4_instance_resolve = false 
        v4_name_convert = { 
                host = { 
                        rcmd = host 
                        ftp = ftp 
                } 
                plain = { 
                        something = something-else 
                } 
        } 
        fcc-mit-ticketflags = true 
  [realms] 
        DOMINIO.COM.BR = { 
        kdc = DOMINIO.COM.BR 
        admin_server = DOMINIO.COM.BR 
        default_domain = DOMINIO.COM.BR 
        } 
  ----------------------------------------------------------------------------------------- 
/etc/likewise-open/likewise-krb5-ad.conf 
  [libdefaults] 
    default_tgs_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC 
    default_tkt_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC 
    preferred_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC 
    dns_lookup_kdc = true 
  [libdefaults] 
        default_realm = DOMINIO.COM.BR 
    [realms] 
        DOMINIO.COM.BR = { 
        kdc = DOMINIO.COM.BR 
        admin_server=DOMINIO.COM.BR 
        } 
    [domain_realms] 
        dominio.com.br = DOMINIO.COM.BR 
        .dominio.com.br = DOMINIO.COM.BR 
  ----------------------------------------------------------------------------------------------- 
   --  
  Thank you

---

### Post by atworkwithjf on 2011-02-16
Are you running Samba on this server as well?

---

