---
title: "OpenLDAP + PHP5 problem"
date: 2012-05-24
forum: General Help
---

### Post by asteway on 2012-05-24
Dear All,

I used this very simple script which I found on PHP Manual to to bind to my OpenLDAP (2.4.23) server (Ubuntu 10.04 LTS) via PHP.

```

<?php
$ldapcon = ldap_connect("localhost")
    or die("Could not connect to LDAP server.");
if ($ldapcon) {

    // binding anonymously
    $ldapbind = ldap_bind($ldapcon);

    if ($ldapbind) {
        echo "LDAP bind anonymous successful...";
    } else {
        echo "LDAP bind anonymous failed...";
    }
}
?>

```I always get a failure for a reason that's not clear to me. Everything is running smoothly except this hiccup. ldap_connect() or ldap_bind() doesn't seem to be working. I can also connect from phpldapadmin without a problem. Can someone please help?

---

### Post by asteway on 2012-06-21
Just solved it! The problem was I am using LDAPv2 code while running LDAPv3. I added the code

 ```
 ldap_set_option($ldapconn, LDAP_OPT_PROTOCOL_VERSION, 3);
```

and all was good!

---

### Post by asteway on 2012-06-21
Just solved it! The problem was I am using LDAPv2 code while running LDAPv3. I added the code

 ```
 ldap_set_option($ldapconn, LDAP_OPT_PROTOCOL_VERSION, 3);
```

after the connection tag and all was good!

---

