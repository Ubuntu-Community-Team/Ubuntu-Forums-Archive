---
title: "ubuntu and ldap problems"
date: 2010-06-10
forum: General Help
---

### Post by beowulf1416 on 2010-06-10
I've set several PCs as clients for ldap authentication. I can authenticate and login fine but I cannot change passwords.
passwd gives me this error:

```
Enter login(LDAP) password: 
passwd: Authentication token manipulation error
passwd: password unchanged
```

ldappasswd gives me this error:

```
ldappasswd -W -D "cn=xxxx,ou=people,dc=xxx,dc=com" "uid=xxx"
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)
```

any thoughts?

---

