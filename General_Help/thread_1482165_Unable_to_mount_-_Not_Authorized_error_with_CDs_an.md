---
title: "Unable to mount - Not Authorized error with CDs and USB drives"
date: 2010-05-13
forum: General Help
---

### Post by Locke2053 on 2010-05-13
I am running 10.04 Lucid Lynx 64 bit.

Whenever I insert a CD or USB flash drive, I get the error "Unable to mount - Not Authorized". 

I can, however, mount these things by using the mount command from the console as root. I suspect that either the component of Lucid which is responsible for automounting has a bug, or there is some kind of permissions bug with the way Ubuntu sets up the primary user.

Does anyone else have this problem? Is there a workaround? Should I file a bug report?

---

### Post by hannon on 2010-05-13
I would try to change the permissions recursively on the mount directory.

---

### Post by Locke2053 on 2010-05-13
Which directory does the automounter use?

---

### Post by pqwoerituytrueiwoq on 2010-05-13
happened to me once something did not start during the boot process i had less rights than i should
i could not do anything with out being root
including using the menu to reboot
i logged in as root and rebooted

---

### Post by Locke2053 on 2010-05-14
This error went away with the latest updates.

---

### Post by TheRoot on 2010-05-20
> **Locke2053 said:**
> This error went away with the latest updates.

Me having the same issues :(

---

### Post by marcos.macedo on 2010-05-27
I had the same problem. It have been gone with some update a week ago and came back with the last update.

Maybe we should post a but report.

---

### Post by hedge.hog on 2010-06-07
> **marcos.macedo said:**
> I had the same problem. It have been gone with some update a week ago and came back with the last update.

Maybe we should post a but report.
Ditto

---

### Post by shrimpy89 on 2010-06-11
This suddenly affects me too.  wtf

---

### Post by vatos on 2010-06-13
Same problem here with usb flash drives and usb hard disk drives, every time i connect something i get unauthorized error

---

### Post by tzily on 2010-06-21
> **shrimpy89 said:**
> This suddenly affects me too.  wtf

+1
oh common, i was just happy with my ubuntu and BANG

---

### Post by gseaborn on 2010-06-21
Everything has been working for me for the last couple of weeks.  I log in this morning, and plug in my USB device and am no longer able to mount.  I changed my account to administrator from custom.  I don't see any clear answer on how to fix this.   Some posts referred to change Properties, but am not sure where that is...bit of a newbie with Linux (Ubuntu)--sorry!  Any assistance would be appreciated!  Greg

---

### Post by tzily on 2010-06-21
> **Locke2053 said:**
> This error went away with the latest updates.

UPDATE: This actually worked for me, thank you.
I've already tried the other method, but it's outdated, the box was checked anyway on my user.
So looks like this is fixed for now.

---

### Post by Tteddo on 2010-07-02
I just ran into this on a new install and all the updates fixed it- FYI.

---

### Post by victorhooi on 2010-07-14
heya,

I've got Lucid 10.04 64-bit, on a VMWare ESXi, and I'm getting the same issue as well, when trying to mount the VMWare Tools virtual ISO.

```
Unable to mount VMware Tools
Not Authorized
```

Cheers,
Victor

---

### Post by voooza on 2010-07-31
Hi,
I was experiencing the same problem. 
The cause in my case was probably experimenting with multiple desktop enviroments.

When i uninstaled other DE and kept only gnome and performed:
 ```
sudo apt-get autoremove
```
things work fine again.

Hope this helps to others as well.

---

### Post by d0.higgs on 2010-08-26
I haven't updated my system for sometime,
I updated to day and I am unable to mount my external HDD!

Could any one solve this problem or traced it back to its origin?

~d0

---

### Post by Meltedfusion on 2010-09-15
Hey everyone. 
I am having this issue as well.
Its an external HDD. I just switched users and bam this sucker is locked down tight.
I ran an update today for the most recent updates dont know if they are related... has anyone figured this out yet?
If i find a solution somewhere i will post it here.

****
Okay i got it to work... So this happened after i switched users. Once i logged the other user off and logged back into my log in neither one of us had access to the drive. 
Shutdown didnt work either. I had manually hold the power button down. After that i unplugged the external. After  I powered the pc back on i powered on the external logged in and viola she came back on..
Hope this helps anyone else that might encounter this issue.

---

### Post by disciplefk on 2010-09-23
any more solutions? my machine is doing the same after updates.  Been fighting with dual monitor setup as well after update.  Also when I go to shutdown, takes me to login screen, does not shutdown pc.  Crippling updates!

---

### Post by lcl on 2010-09-26
Linux choboo-desktop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux
AMD x4 640


I got the following problems
Can't shutdown
Can't mount USB drive, Not Authorized.
The Advanced Settings button won't respond under System, Administration, Users and Groups

If I did a reset--to cold boot, it works.  But if I were to remove the USD media, a SDHC card in my case, then it stops working again.  

I have a clean install and immediately checked and installed all the updates.

---

### Post by blogmaniak on 2010-10-01
Hello everyone .. i was having the same issue, both internal and external hdd were not mounting (Not authorized), could not launch the advanced menu under user/groups. I ran the full update, which updated something with avahi, which I also saw in system logs where it said permissions dropped (under avahi).

After running full update, the issue was fixed and all my mounts are loading properly. Hope this works for everyone else!!

Update:There was a power outage and system had a hard shutdown. Since restarting I have lost the permissions all over again.
Please any idea for a fix? I cannot mount, cannot shutdown and sound does not work either.

Update: Just did reboot from cmd, twice and second time the system loaded with proper permissions.

---

### Post by lcl on 2010-10-08
Seems like only a handful of users are experiencing this anomaly.  Sometimes, I just can't reboot or shutdown through the GNOME menu.

---

### Post by minnoit on 2010-11-28
I installed ubuntu desktop and subsequently Lubuntu. Then I had the same problem and I could not fix it. Reinstalling the system, the problem returns. My solution was [http://www.linuxmint.com/edition.php?id=60](http://www.linuxmint.com/edition.php?id=60)

---

### Post by Hugs on 2010-11-28
i don't know if this can help, but i had the same problem on Arch Linux, the solution was to add a ck-launch-session command to the exec line in .xinitrc

Like this:
exec gnome-session
Changed to:
exec ck-launch-session gnome-session

Then i was able to mount using other users than root.

---

### Post by minnoit on 2010-11-28
I had read of this solution on a forum of Arch Linux and tried to no avail. Has anyone solved reinstalling policy-kit (there's a thread on launchpad). I tried this but I have not resolved.
In my case, the problem occurred after the first update of Lubuntu. At that point, even Gnome gave the same problems.Ascolta
Trascrizione fonetica

**Dizionario - [Visualizza dizionario dettagliato]("http://www.google.it/dictionary?source=translation&hl=it&q=&langpair=it%7Cen")**


**Traduci qualsiasi sito web**


[LIST]
[*][The Washington Post]("http://translate.google.it/?hl=it&sl=en&tl=it&sugg=w&hints=true&q=http://www.washingtonpost.com/")-Stati Uniti
[*][Berlingske.dk]("http://translate.google.it/?hl=it&sl=da&tl=it&sugg=w&hints=true&q=http://www.berlingske.dk/")-Danimarca
[*][Museo del Prado]("http://translate.google.it/?hl=it&sl=es&tl=it&sugg=w&hints=true&q=http://www.museodelprado.es/")-Spagna
[*][El Confidencial]("http://translate.google.it/?hl=it&sl=es&tl=it&sugg=w&hints=true&q=http://www.elconfidencial.com/")-Spagna
[*][Komika Magasin]("http://translate.google.it/?hl=it&sl=sv&tl=it&sugg=w&hints=true&q=http://komikamagasin.se/")-Svedese
[*][Nord-Cinema]("http://translate.google.it/?hl=it&sl=fr&tl=it&sugg=w&hints=true&q=http://nord-cinema.com/")-Francia
[*][Spiegel Online]("http://translate.google.it/?hl=it&sl=de&tl=it&sugg=w&hints=true&q=http://www.spiegel.de/")-Germania
[*][Elle]("http://translate.google.it/?hl=it&sl=fr&tl=it&sugg=w&hints=true&q=http://www.elle.fr/elle/")-Francia
[*][Zamalek Fans]("http://translate.google.it/?hl=it&sl=ar&tl=it&sugg=w&hints=true&q=http://www.zamalekfans.com/")-Arabo
[*][Gotujmy.pl]("http://translate.google.it/?hl=it&sl=pl&tl=it&sugg=w&hints=true&q=http://www.gotujmy.pl/")-Polacco
[*][&#30406;&#26685;]("http://translate.google.it/?hl=it&sl=ja&tl=it&sugg=w&hints=true&q=http://bonsai.ne.jp/")-Giappone
[*][Sueddeutsche.de]("http://translate.google.it/?hl=it&sl=de&tl=it&sugg=w&hints=true&q=http://www.sueddeutsche.de/")-Germania
[/LIST]


   **Fai di più con Google Traduttore**


[LIST]
[*][[IMG]http://www.google.com/images/icons/illustrations/viking_hat-y80.png[/IMG]]("http://translate.google.it/about/intl/it_ALL/tour.html#professional")**Vorresti che i tuoi fan norvegesi potessero leggere il tuo blog?** Installa l'[elemento Google Traduttore]("http://translate.google.it/about/intl/it_ALL/tour.html#professional") per una facile traduzione.
[*][[IMG]http://www.google.com/images/icons/illustrations/translate_webpage-lb80.png[/IMG]]("http://translate.google.it/about/intl/it_ALL/tour.html#explore")**Ti sei bloccato davanti a un sito web straniero?** Scarica [Google Chrome]("http://translate.google.it/about/intl/it_ALL/tour.html#explore"), un browser rapido e sicuro con funzionalità di traduzione integrata.
[*][[IMG]http://www.google.com/images/icons/illustrations/sushi-80.png[/IMG]]("http://translate.google.it/about/intl/it_ALL/tour.html#search-sushi")**Cerca le migliori ricette di sushi al mondo, in giapponese!** Sprigiona la potenza della [Ricerca tradotta]("http://translate.google.it/about/intl/it_ALL/tour.html#search-sushi") di Google.
[*][[IMG]http://www.google.com/images/icons/illustrations/translate_robot-lb80.png[/IMG]]("http://translate.google.it/about/intl/it_ALL/")**Linguisti, robot o alieni?** Ottieni informazioni sulla [tecnologia]("http://translate.google.it/about/intl/it_ALL/") di Google Traduttore e su come puoi aiutarci a migliorarla.
[/LIST]

---

