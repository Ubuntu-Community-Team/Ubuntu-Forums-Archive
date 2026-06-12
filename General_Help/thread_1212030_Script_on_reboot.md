---
title: "Script on reboot"
date: 2009-07-13
forum: General Help
---

### Post by brunoskrebs on 2009-07-13
Hello,

I'm running a ubuntu server that has Glassfish installed on it, and every single time that I reboot my system I have to do the following steps:
```

cd /var/lib/glassfishv2/domain
asadmin start-domain domain1
admin <-- "glassfish asks for the admin user"
******** <-- "glassfish asks for the admin password

```

Is there a script that I can use to automate this?
I have searched on internet, and found a few links, but no success so far.

Thanks in advance.

Bruno Krebs

---

### Post by Keith Hedger on 2009-07-13
Add the commands to /etc/rc.local

---

### Post by brunoskrebs on 2009-07-13
Ok, but what about the admin username and password?

Because glassfish prompts me asking for these informations.

If I add these 4 lines ("cd ...", "asadmin ...", "admin" and "password") it will work?

---

### Post by brunoskrebs on 2009-07-13
Well I just tested and it does not work...

---

### Post by Keith Hedger on 2009-07-13
You can try making a script and putting it in /etc/init.d (don't forget to make it executable) then put a sym link to it in /etc/rc0.d (for example, the number refers to the run level I believe) and it should execute ok look at the other scripts in /etc/init.d for the syntax.

P.S. how you feed the user name and password to glassfish I can't help you with (what is glassfish?)

---

### Post by brunoskrebs on 2009-07-13
So I make this script but it still going to be prompting the user and password every time I reboot?

Glassfish is a Java EE aplication server.

---

### Post by Keith Hedger on 2009-07-13
I don't have glassfish installed  but you could try looking in the man page and see if there is an option to set the user/password from the command line or failing that you could run it as a HERE script, for more details check out the advanced scripting guide from the repos.

---

