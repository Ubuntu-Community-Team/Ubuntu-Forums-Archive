---
title: "Evolution with Exchange"
date: 2006-04-03
forum: General Help
---

### Post by jonnymccullagh on 2006-04-03
I need some help accessing mail and calendar which reside on an Exchange server.
I have installed evolution and evolution-exchange and I have visited : K > Debian > Apps > Net > MS Exchange Setup Wizard
In the wizard I entered (example): 
Server name: 192.168.1.40
Port: 143
User name: mydomainloginname
Password: mydomainloginpass
I then click OK and run Evolution. Then Edit > Preferences > Account > Add...

When adding an account I enter my name and email address then choose Microsoft Exchange as the Server type.
Once I choose exchange I get an input box below asking for Username. I again enter my domain login username but the 'Forward' button is disabled. I also try MyUsername@192.168.1.40 and MyUsername@servername

I cannot click forward until I change the server type from exchange to something else e.g. IMAP and back again to exchange.

However, when I try to retrieve my mail I cannot. I am asked for my password and get the following error:
"Error while scanning folders in Exchange Server" Could not authenticate to server. (Password incorrect?)

Incidentally the box asking for the password always has an @ symbol at the end e.g. Password for jonny@192.168.1.40@

Can anyone offer any help - I need tobe able to see my mail and calendar?
thanks,
jonny

---

### Post by freelsjd on 2006-04-03
Here, the login name is 

domainname\loginuid

---

### Post by jonnymccullagh on 2006-04-03
Thanks - I will try that when I get back to work on Wednesday morning.
Cheers, j

---

### Post by jonnymccullagh on 2006-04-05
I have tried using:
mydomain\jonny
but I get similar problems.
1. Once I choose exchange I get an input box below asking for Username. I  enter mydomain\jonny but the 'Forward' button remains disabled
2. When Evolution asks for the password it asks for "Enter password for mydomain\jonny@"
I can't find any info on the web about setting up evolution with exchange.

When I set up the account as IMAP it works gets the mail but I also need the calendar.
Any help is appreciated, thanks,
jonny

---

### Post by freelsjd on 2006-04-05
Perhaps your Microsoft site installation is different then here.  I have read all kinds of issues with this at various sites.  Is your domain name capitalized; 

MYDOMAIN\jonny

Also, have you tried instead

[email]jonny@mydomain.what[/email]ever 

?

---

### Post by nelsonb73 on 2006-04-11
Try Installing the package evolution-plugins, I was having the same trouble when I noticed in synaptic that this package had the helpful  -exchange-account-setup plugin.... Maybe this should be a dependency if you install evolution-exchange...

---

### Post by jonnymccullagh on 2006-04-12
Thanks I think you are right,
I reinstalled evolution and when going through the Account setup for exchange I now get asked for the OWA (Outlook Web Address) so it is working for me now - I wasn't being asked for this before.

So now I am able to connect and see my emails but it crashes quite fequently although I think this is because I have thousands of messages in my inbox (I know, I know - I'll sort it out tomorrow).

Relying on Outlook for the time being but I'll get there - thanks for your help.

Incidentally, the   K > Debian > Apps > Net > MS Exchange Setup Wizard
I think this has nothing to do with evolution and is something to do with KOffice?

Cheers,
jonny

---

### Post by ycng76 on 2006-04-24
[QUOTE=jonnymccullagh]I need some help accessing mail and calendar which reside on an Exchange server.
I have installed evolution and evolution-exchange and I have visited : K > Debian > Apps > Net > MS Exchange Setup Wizard
In the wizard I entered (example): 
Server name: 192.168.1.40
Port: 143
User name: mydomainloginname
Password: mydomainloginpass
I then click OK and run Evolution. Then Edit > Preferences > Account > Add...

When adding an account I enter my name and email address then choose Microsoft Exchange as the Server type.
Once I choose exchange I get an input box below asking for Username. I again enter my domain login username but the 'Forward' button is disabled. I also try MyUsername@192.168.1.40 and MyUsername@servername

I cannot click forward until I change the server type from exchange to something else e.g. IMAP and back again to exchange.

However, when I try to retrieve my mail I cannot. I am asked for my password and get the following error:
"Error while scanning folders in Exchange Server" Could not authenticate to server. (Password incorrect?)

Incidentally the box asking for the password always has an @ symbol at the end e.g. Password for jonny@192.168.1.40@

Can anyone offer any help - I need tobe able to see my mail and calendar?
thanks,
jonny[/QUOTE]


Sorry, I'm a newbie and I've just installed kubuntu desktop.
How to get the K>Debian menu.... I don't see mine here?

---

### Post by jonnymccullagh on 2006-04-24
I got it (and many other goodies) using Automatix.(I don't know the package name for sudo apt-get install)
Give it a try and tick the box for the Debian menu.
I have found that often when I install software using Synpatic etc that the menu link is under the Debian menu rather than within my main K menu - especially the gnome software. 
The K Control Centre is also under Debian which I think is useful to have.
All the Best,
jonny

---

### Post by lilbudda on 2007-06-09
I fixed my issue but going to the plug-ins (edit -> plugins) and enabling Exchange.

---

