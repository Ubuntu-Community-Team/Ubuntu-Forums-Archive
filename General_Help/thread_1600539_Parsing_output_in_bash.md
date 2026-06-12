---
title: "Parsing output in bash"
date: 2010-10-19
forum: General Help
---

### Post by linux-hack on 2010-10-19
Hi there everyone. I rely need your help with a script of mine.

For example I want to make querys to an LDAP server and get back the users that hav access to a given server. Or show all the servers that a user has access to. I use ldapsearch for that.

But I'd like to parse a simply as possible the output that looks like this :

```

 dc=lv1002va,ou=domain,ou=hosts,dc=company,dc=ch
 dc=lv1002vb,ou=domain,ou=hosts,dc=company,dc=ch
 dc=lv1002vc,ou=domain,ou=hosts,dc=company,dc=ch
 dc=lv1002vd,ou=domain,ou=hosts,dc=company,dc=ch
 dc=li1001v,ou=domain,ou=hosts,dc=company,dc=ch
 dc=slv0266v,ou=domain,ou=hosts,dc=company,dc=ch
 dc=slv0075i,ou=domain,ou=hosts,dc=company,dc=ch
 dc=livve80v,ou=domain,ou=hosts,dc=company,dc=ch
 dc=solve77v,ou=domain,ou=hosts,dc=company,dc=ch

```
But I just want the par where is the (lv1002va) for example but for all of the output. So I'd like to get from this list all the servers after the first dc=[lv1002va] and nothing else.

How can I do that more simply then this :
```
ldapsearch -LLL "cn=group_name" cn member | awk '/(=l.*|=s.*)$/ {print $2}' | awk -F"=" '{print $2}' | cut -d"," -f1
```

Thanks a lot for your help.

---

### Post by amauk on 2010-10-19
Try this

```
ldapsearch -LLL "cn=group_name" cn member | cut --delimiter=',' -f1 | cut --delimiter='=' -f2
```

---

### Post by linux-hack on 2010-10-20
Better but its still giving me other infos then the hosts.

---

### Post by linux-hack on 2010-10-20
well I tried this : 

```

ldapsearch -LLL "cn=group_name" cn member | cut --delimiter=',' -f1 | cut --delimiter='=' -f2 | awk '/^(l|s)/ {print $1}'

```

---

