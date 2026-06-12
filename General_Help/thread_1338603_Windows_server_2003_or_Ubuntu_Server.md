---
title: "Windows server 2003 or Ubuntu Server?"
date: 2009-11-26
forum: General Help
---

### Post by deanjames on 2009-11-26
Hi guys im new here just getting into setting a server up ive only ever had the other side of it, currently studying cisco, but have been asked to set up a server and talk about the advantages and disadvantages of windows 2003 and ubuntu wondering if anyone can help me. I know ubuntu is open source free ect so just wondering on the other advantages / disadvantages hope you can help

Dean

---

### Post by Spiritof76 on 2009-11-26
I have only played with Ubuntu server, and and am not very good at it, but Ubuntu seems very powerful and makes the best use out of the available resources. The disadvantages to Ubunbtu is that it has been dificalt for me to find information aplicable to my particular build, and figuring out whether tutorials and help is applicable to my build (Karmic)

---

### Post by Digikid on 2009-11-26
Linux: No MAJOR viruses
Windows:  Spyware, hacking, Viruses, BSOD, Freezing,

---

### Post by Anonymousable on 2009-11-26
You're not likely to get any non-biased answers here ;)

I'm talking from experience here:
Situation: You have some new hardware.
Ubuntu - Either hardware works, it doesn't work, or you can write a driver for it.
Windows - It works or it doesn't work even when you've looked through 200 badly-organised pages of help about it.

Situation: Boot times.
Ubuntu [SIZE=1](9.10 Karmic Koala, see my signature for hardware)[/SIZE]: 5 seconds
Windows XP: 80 seconds.
I know this is a somewhat unfair comparison what with the versions.

Situation: Log on. Waiting for it to become ready
Ubuntu: Usually 2 seconds, I have a pdf on my desktop that it insists on thumbnailing, making 12 seconds
Windows: No idea when it's ready. It always seems as slow.

These are just 3 situations, I would post more but can't come up with any :P

---

### Post by blueridgedog on 2009-11-26
Having run each, I would say that a Linux server is more easily managed, allows you to run a variety of open source server products (free radius - which plays very well with cisco, apache, sendmail, procmail, mysql, bind and on an on).  Much of this is installed by default.  A Linux server also has no default graphical environment, making all cpu cycles available for server.  The Linux server will generally be immune from viruses and malware and will has a state of the art packet filtering tool installed by default.

To compare however, you really need to have a mission in mind.  If you need an AD server for a workgroup, then 2003 would be better, but if you want a file server and mail server, then Linux would win in my opinion.  Another factor is who will administer the system.  If they have good windows skills, then giving them something the know about is better than asking them to improperly admin a box that will suffer from the lack of experience.

---

### Post by deanjames on 2009-11-26
cool when you say no major viruses what do you mean?

Il read into them any other points i should think about? 

From what ive gathered Windows 2003 is suppose to be more user friendy offering more wizards in comparison to ubuntu is this the case

what programs are available as extras in ubuntu server ?

---

### Post by deanjames on 2009-11-26
> **blueridgedog said:**
> Having run each, I would say that a Linux server is more easily managed, allows you to run a variety of open source server products (free radius - which plays very well with cisco, apache, sendmail, procmail, mysql, bind and on an on).  Much of this is installed by default.  A Linux server also has no default graphical environment, making all cpu cycles available for server.  The Linux server will generally be immune from viruses and malware and will has a state of the art packet filtering tool installed by default.

To compare however, you really need to have a mission in mind.  If you need an AD server for a workgroup, then 2003 would be better, but if you want a file server and mail server, then Linux would win in my opinion.  Another factor is who will administer the system.  If they have good windows skills, then giving them something the know about is better than asking them to improperly admin a box that will suffer from the lack of experience.


for active directory why would windows be better?

---

### Post by neerajadsul on 2009-11-26
Linux Servers - [LIST]
[*]minimal downtimes during patches.
[*]                excellent console administrative capability
[*]                server can be stripped down to minimal specific for the task
[*]                OS it self doesn't hog the system resources
[*]                clustering possible
[*]                administrators can patch bugs,modify source - open source
[*]                most of the times help is available on internet for FREE - forums, IRC, how to's, mailing lists
[*] technical support options also available  - Novell, Red Hat, Ubuntu, Mandriva etc.
[/LIST]

Windows Servers - just add negation to above
                  [LIST]
[*]only advantage is - for skill less skilled administrators GUI administration jobs
[*]technical support from MS may be useful (but I am not sure about time spent in doing that)
[*]most of MS technologies need Windows servers
[/LIST]

---

### Post by J V on 2009-11-26
There is a reason linux holds 70% of the server market share and windows only holds 10%...

To sum it up:

[LIST]
[*]Quick bugfixes **vs** weekly/monthly
[*]No restarts **vs** guarenteed downtime
[*]No virusses **vs** required antivirus (and slowdown)
[*]Designed for multiple users permission system **vs** complicated permission system (That doesn't really work)
[*]Can run *forever* without a reboot **vs** weekly downtime *or* security hole, take your pick
[*]Apache server is the norm for hosting and most systems will be incompatable with IIS
[/LIST]
Note I say linux rather than specifically ubuntu, red hat is considered the norm for hosting if I recall, but ubuntu will do fine

I read a great testimonial about a guy who worked at hosting buisnesses that kept going bankrupt when they took on windows servers :)

Can't find it... look up linux server testimonials for more :P

---

### Post by deanjames on 2009-11-26
i see where your coming from now this is just the information i was after can anyone point me in the direction of any decent reading 

Massive thank you guys

---

### Post by blueridgedog on 2009-11-26
> **deanjames said:**
> for active directory why would windows be better?

AD is an MS creation and, though you can do it with Linux, I have never seen an implementation that was as easy or reliable as an MS server domain controller.

---

### Post by J V on 2009-11-26
couldent find that testimonial...

[http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux](http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux) - Basicly says linux is superior in every way for someone advanced enough to run a server, can't find server specific one...

---

### Post by deanjames on 2009-11-26
thanks a lot guys il take a look

---

### Post by distro.tv on 2009-11-26
Linux is freedom. You can install Linux where you want to change it in any way, depending on your needs. Using Linux is focused on how to implement it and not on how many you have to pay for another license.

---

### Post by deanjames on 2009-11-26
anyone got any more information for me regarding advantages and disadvantages

---

### Post by deanjames on 2009-11-30
btt

---

