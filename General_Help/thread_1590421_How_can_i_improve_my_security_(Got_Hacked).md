---
title: "How can i improve my security? (Got Hacked)"
date: 2010-10-07
forum: General Help
---

### Post by silentrock on 2010-10-07
TOday i messed with some hard hacker which i mistreat,he got angry and demostrated that Ubuntu is not really as secure as i thought.

He took all my passwords,paypal,FaceBook,Hotmail.ALL of them.

Any way i can set up any firewall or protection agaisnt this?


I think he exploited via IP. THanks.

---

### Post by Merthod on 2010-10-07
You've answered yourself. Ubuntu comes with its Firewall uninstalled. So install it and configure it (ufw).

---

### Post by silentrock on 2010-10-07
Umm enabled UFW and all that thanks,i hope this doesnt repeat :)

---

### Post by Awareness on 2010-10-07
its hard to say what are you doing wrong without looking at your computer or network... there are lots of ways in. Not only ubuntu oriented...

but...

never install anything untrusted (if you know nothing, i would never ever install anything out of the repositories)

try to 'nmap -p1-65550 localhost' to tell what extra services you are running. If you dont have a router before your connection try to nmap your public ip.

run some rootkit on your computer.

dont use words for passwords.

dont leave open ssh if you dont use it.

etc...
...

---

### Post by 3Miro on 2010-10-07
> **Merthod said:**
> You've answered yourself. Ubuntu comes with its Firewall uninstalled. So install it and configure it (ufw).

Not true! The only thing that you are missing by default is the tool to adjust the firewall settings. By default, Ubuntu doesn't listen to any ports, so there is no need to adjust the firewall. This can become an issue only if you run services like ssh, apache, nfs and so on. Maybe Samba as well.

To "improve" your security, you first have to figure out what went wrong. Did you install anything untrusted? Do you have Samba or some other service installed? Have you given your password to anyone? 

Also, what kind of network are you running on? As someone mentioned, there are ways to "hack" passwords that are related to the network and not Ubuntu (basically there is nothing that the OS can do about it). Did you connect to his own home network and then access those web-pages from there?

---

### Post by Merthod on 2010-10-07
Yeah, I was wrong. It is just disabled but I had to install the interface so I got mixed up.

I'm running several services and the best practice here is to close everything except what you really need to the right program.

Here's the ubuntu doc: [https://help.ubuntu.com/10.04/serverguide/C/firewall.html]("https://help.ubuntu.com/10.04/serverguide/C/firewall.html")

---

### Post by NDLunchbox on 2010-10-07
> **Awareness said:**
> 
never install anything untrusted (if you know nothing, i would never ever install anything out of the repositories)
...

Are you saying the Ubuntu repositories are unsafe or do you mean never install anything outside of the repositories?

---

### Post by ankspo71 on 2010-10-08
Hi,
Try keepassx for storing your passwords, and change all of your website passwords immediately of you haven't done so already. Change your system passwords too. Keepassx is cross platform and has 2 types of encryption.

I'm not too security-experienced in Linux (although that's about to change)... so all I can offer is these links on security related things to read.

Ubuntu Security:
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[https://help.ubuntu.com/community/InstallingSecurityTools](https://help.ubuntu.com/community/InstallingSecurityTools)

GUFW, UFW, and IPtables:
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) (for advanced users)

Linux (in general) security apps
[http://www.linuxlinks.com/article/20080429140249467/Security.html](http://www.linuxlinks.com/article/20080429140249467/Security.html)

Hope this helps.

---

### Post by Awareness on 2010-10-08
> **NDLunchbox said:**
> Are you saying the Ubuntu repositories are unsafe or do you mean never install anything outside of the repositories?

I mean never install something outside the repositories unless you know what you are doing.

For example, in my case, i dont trust all those links that show up in omg ubuntu! blog or that kind of webs. Or most ppas. I dont think they meant bad or evil. I just i dont know where they come from.

---

### Post by 3Miro on 2010-10-08
> **Awareness said:**
> I mean never install something outside the repositories unless you know what you are doing.

For example, in my case, i dont trust all those links that show up in omg ubuntu! blog or that kind of webs. Or most ppas. I dont think they meant bad or evil. I just i dont know where they come from.

The official repos are safe, everything else is unsafe. That is not to say that everything else is necessarily bad, just that you have to be very careful and that you are taking a risk.

---

### Post by Peter09 on 2010-10-08
The interesting thing here is - how did he do it - Until you have some idea then you do not know which door to shut :(

---

### Post by KingNeil on 2010-10-08
This thread is way too vague.

You could have had weak passwords. You could have posted your passwords online. You could have been using rogue software. There are too many options. To conclude that Ubuntu is unsafe is not the right conclusion. And I'm definitely not one of these people that says Ubuntu is perfect blah blah blah. But seriously. Not enough information provided in this thread.

---

### Post by bvanaerde on 2010-10-08
> **KingNeil said:**
> You could have had weak passwords. You could have posted your passwords online.
Most definitely one of these options KingNeil mentioned, and if I had to guess, it would be the second option. Phishing has replaced the virus from being the biggest virtual threat, imo.

---

### Post by iiiears on 2010-10-08
That sounds truly awful. 

If you are feeling like an intrepid operating system explorer investigate.
Virtual Machines
PGP Gpg
TrueCrypt
Apparmor
Tripwire
Selinux
DigSig
GNU Debugger

Carefully consider if you really need Samba and printer sharing, browser plugins and javascript..

Take a peek at Bruce Schneiers article on DNS. about 15mins to read and much longer to understand the implications.

---

### Post by NDLunchbox on 2010-10-08
> **Awareness said:**
> I mean never install something outside the repositories unless you know what you are doing.

For example, in my case, i dont trust all those links that show up in omg ubuntu! blog or that kind of webs. Or most ppas. I dont think they meant bad or evil. I just i dont know where they come from.

Thanks for clearing that up... I sometimes recompile things from source, but I ALWAYS go to the project's site for download links.  I've done this for things like digitemp, OpenSSH, JTR and TrueCrypt.  I use the repositories whenever possible though...

Another thing to think about... learn some white hat skills and pentest yourself.  I use JTR and Nessus (along with commercial scans) for myself and my company.  Read [http://www.amazon.com/Network-Security-Assessment-Know-Your/dp/0596510306/ref=sr_1_1?ie=UTF8&qid=1286545662&sr=8-1]("http://www.amazon.com/Network-Security-Assessment-Know-Your/dp/0596510306/ref=sr_1_1?ie=UTF8&qid=1286545662&sr=8-1")
and [http://www.amazon.com/Security-Warrior-Cyrus-Peikari/dp/0596005458/ref=sr_1_3?ie=UTF8&qid=1286545662&sr=8-3]("http://www.amazon.com/Security-Warrior-Cyrus-Peikari/dp/0596005458/ref=sr_1_3?ie=UTF8&qid=1286545662&sr=8-3")

Also, turn on the "encrypt my home directory" option.

---

### Post by HermanAB on 2010-10-08
Hmm, something fishy here...

For anybody to get access to your machine,you must have a service running that can be exploited.  So, my guess is that you have VNC, SSH or FTP running with a kewl four letter password or some such.

If you refrain from running services that you don't understand and use proper passwords, then you won't get hacked.

---

### Post by The Cog on 2010-10-08
> **silentrock said:**
> 
He took all my passwords,paypal,FaceBook,Hotmail.ALL of them.

Did he get your Ubuntu password? If not then my guess is that your hotmail account got hacked somehow, and he then used his access to that to change the passwords on all the other web sites. It seems that lots of hotmail accounts are being hacked at the moment. And if your hotmail account is the one used as the email contact point for things like facebook forgotten passwords then he's got the lot.

---

### Post by silentrock on 2010-10-09
My Ubuntu password is ok,but everything was remotely,he is miles away from me.

---

