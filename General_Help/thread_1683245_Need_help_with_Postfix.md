---
title: "Need help with Postfix"
date: 2011-02-07
forum: General Help
---

### Post by Nailox on 2011-02-07
Im really confused now :( Im trying to install postfix server on localhost and use the SMTP with interspire to send emails (Idk if thats eve possible). So I installed virtualmin on my localhsot to help me configure postfix, because I tried some howtos on postfix but with no luck. I have a domain name which is forwarded to my IP. I managed to configure postfix in virtualmin - whe I run system check it says postfix mailserver is configured correctly, but suexec is configured to run from /var/www and my default directory is /home so I cant run cgi and php scripts on the host as owner. Idk if this is relevant ot not. When I go to 'status' in virtualmin, postfix is off and I cant start it. Also when I run a ports scan from a site on my IP it says poer 25 is closed. In interspire i set SMTP settings to be username: the user in virtualmin for email accounts and his password. I tried all combinations of users, domains, and passwords. It says it cant connect to the remote server. Im not sure id my ISP blocks port 25 so i tried to redirect the port using this howto [http://www.5dollarwhitebox.org/wiki/index.php/Howtos_Basic_IPTables#Port_Redirects](http://www.5dollarwhitebox.org/wiki/index.php/Howtos_Basic_IPTables#Port_Redirects) but no luck. The thing that confuses me is that both interspire and virtualmin are on the same host and they try to connect each other so I cant really understand this. Any help how to make this work? Or any other ideas how to setup SMTP on my desktop and send emails ?

---

### Post by ahsan101 on 2011-02-07
Probably a clean install of postfix can help you out there!

---

### Post by ahsan101 on 2011-02-07
Have you tried the postfix standard configurations from their website?

---

### Post by dcstar on 2011-02-08
> **Nailox said:**
> Im really confused now :( Im trying to install postfix server on localhost and use the SMTP with interspire to send emails (Idk if thats eve possible). So I installed virtualmin on my localhsot to help me configure postfix
.........
Any help how to make this work? Or any other ideas how to setup SMTP on my desktop and send emails ?

```
sudo dpkg-reconfigure postfix
```

Select "Internet" and all other relevant questions.

---

### Post by weblizist on 2011-02-11
Are you able to connect local to port 25? -> to find out if the problem is ISP related or local.
What are the logs telling you after trying to start postfix? -> Usually they report access vialotions quite verbally.
Did you ever try starting postfix with increased verbosity/debugging level or to work you through the postfix debug check-list ([http://www.postfix.org/DEBUG_README.html](http://www.postfix.org/DEBUG_README.html))

---

