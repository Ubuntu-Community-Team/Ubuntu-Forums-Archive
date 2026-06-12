---
title: "Looking for networked email client like Pegasus mail"
date: 2011-03-18
forum: General Help
---

### Post by PM47 on 2011-03-18
Hi,

I'm (finally) migrating from Windoze to Ubuntu. I'm looking for a network aware email client like Pegasus mail ([www.pmail.com]("http://www.pmail.com")). I currently have Pegasus set up with the mail folders stored on a NAS device and the Pegasus mail client running on each of my workstations, any user (family member) can access their mail from any workstation, simultaneously if necessary, Pegasus implements proper network file locking to prevent multiple access to the files.

I've looked at several of the email clients available for Ubuntu but there's little information available on the network capabilities of these programs. Obviously any of them can (presumably) store their email files on a network shared folder, but this doesn't necessarily mean they are network aware and will work correctly when accessed from multiple workstations.

I'm a little nervous of installing some of these programs to try them out as I'm not yet that familiar with Ubuntu and a bit wary of messing up the system installing and uninstalling programs.

Eventually I'll also be looking to install a local POP3 mail server, I currently use VPOP3 ([www.pscs.co.uk]("http://www.pscs.co.uk")) but that can wait until I'm a bit more familiar with Ubuntu.

Any help would be very much appreciated at this stage in my conversion.

Paul

---

### Post by dragonfly41 on 2011-03-18
I'm in the same boat as you .. newbie to Ubuntu with a crashed Vista OS and Ububtu in dual boot mode.

One of my Vista email clients was Pegasus.   The other was MS Outlook.   So there is an interesting migration problem here to crack.

I have yet to test this idea myself .. but I'm guessing that Pegasus WinPMail.exe might run in Wine at least to migrate the Pegasus files to some native Ubuntu email client.

---

### Post by PM47 on 2011-03-19
I'm resisting loading Wine (or similar) as one of my motives is to escape from Windoze, I suspect if I load Wine I'll just end up running my Windoze apps in Wine and never really get to grips with Linux :-(

Unfortunately most of the email clients I've looked at seem to consider emulating Outlook as a priority - my priority is the networking bit which works very nicely in Pegasus Mail.

I'll let you know if I find anything sensibel.

Paul

---

### Post by PM47 on 2011-04-24
Update - Surprisingly there doesn't appear to be a proper multi-user  network aware email client for Linux, as far as I can find anyway. It's a  shame Pegasus Mail was never ported to Linux. 

The closest  solution I can find is to use an IMAP mail server, which retains the  mail in local folders rather than it being downloaded to the mail client  on each workstation. This also satisfies my requirement for a local  mail server :

I need to be able to collect mail from various  places and make it available to several users on several workstations in  a flexible manner, i.e. each user can use any of the available  workstations to access their mail. The only way to achieve this using  Linux seems to be to use an IMAP Mail Server, I've chosen to use  Dovecot. It appears that two additional programs are needed to make  Dovecot work, I've chosen to use Fetchmail and Postfix. I intend to use  Evolution as the email client.

As far as I can see Fetchmail is  set up to regularly collect mail from the mail servers,using SMPT, and deliver it to  Dovecot, which is listening on port 25. Dovecot sorts and stores the  mail into folders using the 'MailDir' format. Ultimately I want the mail  stored on my NAS device in a heirachical structure, i.e.  ../LinuxMail/Username/.. but for now I'm trying to set the system up on  the local hard drive. Evolution, on any local workstation, can then  connect to Dovecot port 110 to read mail. It  appears Evolution can be  set to IMAP mode where it synchronises it's mail folders with Dovecot,  the mail remains in the folders maintained by Dovecot so is available to  any networked PC at any time.

Evolution is set up to send mail  using SMTP. I'm a little confused here as at present I have Evolution  set up to send mail directly to my Windoze mail server, so what is  Postfix used for ? All the info I've found on Dovecot suggests Postfix  (or SendMail) is required however, so I've installed it as per the  instructions. Also Postfix and Dovecot appear to need to be listening on  port 25, which surely won't work ? Or is this why Postfix is necessary ?

So  far I've got Evolution running with my Windoze mail server with no  problem. I've managed to set up Postfix so I can send a text string from  the command line to my Gmail account via the Windoze mail server, I had  to install 'mailutils' to do this.  Fetchmail is set up so when I run  it with the -c parameter it identifies the mail available on my Windoze  mail server. I'm now trying to set up Dovecot and Evolution to glue the  whole lot together. Note the intention is to eventually replace the  Windoze mail server with this set up, but for test purposes it's  convenient to use the Windoze mail server rather than my ISP.

Question  is - am I going about this in the right way and will it do what I want ?  I'm struggling a bit with all the conflicting instructions available  and the necessity to manually create/edit/modify all the low level  configuration files needed to get this lot to work. The Windoze approach  of providing graphical setup utilities with programs is surely the way  to go ? Fetchmail has a graphical setup utility, but on my PC the text  vanishes under the text boxes to the point where it's not usable, I  resorted to manually editing the config file :-(

I'm slowly making headway on setting this lot up but any comments or pointers would be much appreciated at this point in time.

Thanks

---

### Post by dragonfly41 on 2011-04-24
I'm still having to use Pegasus & MS Outlook on my Windows Vista.

I've read about squirrel ..

[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

Is this an option to add to the list?   However it is webmail.

---

### Post by PM47 on 2011-04-24
I installed Squirell as I too thought it might be a solution. The instructions are so clear that I couldn't even find out how to run it, let alone try it out. It doesn't appear in any of the menus. It looks like you have to connect to it using a web browser, but quite how eluded me completely :-(

---

### Post by dragonfly41 on 2011-04-24
You need to first install Apache + php5

[http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/](http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/)

then install squirrelmail

[https://help.ubuntu.com/community/Squirrelmail#Check%20it%20works](https://help.ubuntu.com/community/Squirrelmail#Check%20it%20works)!

and you should see login page at [http://localhost/squirrelmail](http://localhost/squirrelmail)

---

### Post by PM47 on 2011-04-24
> **dragonfly41 said:**
> You need to first install Apache + php5

[http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/](http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/)

then install squirrelmail

[https://help.ubuntu.com/community/Squirrelmail#Check%20it%20works](https://help.ubuntu.com/community/Squirrelmail#Check%20it%20works)!

and you should see login page at [http://localhost/squirrelmail](http://localhost/squirrelmail)


Yes, I tried all that. If you install Squirrel using the Synaptic Package Manager then Apache etc. is also installed as a dependancy. Unfortunately it doesn't work the other way around when you uninstall Squirrel so I've most likely got some bits that I no longer need still installed.

I think my problem at present is understanding exactly what to put into the config files, getting it wrong, then not being familiar enough with Linux to work out where I've gone wrong. Thre's quite a bit of trial and error going on at prsent  :-(

---

### Post by dragonfly41 on 2011-04-24
I had previously installed LAMP server before trying to add squirrelmail.

I have no requirement to uninstall LAMP server but I've just read that [COLOR=Blue]**tasksel**[/COLOR] can be used for this

[http://ubuntuforums.org/showthread.php?t=1612389](http://ubuntuforums.org/showthread.php?t=1612389)

sudo apt-get install tasksel
sudo tasksel

untick LAMP

I see that tasksel can install a number of packages and there is reference to mail server.

I have no experience of using tasksel yet but might try it to install tomcat.

---

### Post by PM47 on 2011-04-25
I've given up - I've spent all day today wading back and forth through the configuration files trying to fathom out how to set them up. This is the best reference I found ...

[How to Configure an e-mail server with Fetchmail/Postfix/Dovecot]("http://ubuntuforums.org/showthread.php?t=1015150") 

I eventually managed to read mail from my windoze mail server into Evolution, once. When I tried to send mail it ended up back in my inbox and the Send/Receive button in Evolution is now greyed out so I can't send or receive mail any more.

It shouldn't be this difficult to set up a simple network aware email client ! I'll now have to decide if we can work with the restrictions imposed by the standard email clients or give up with Linux completely and put up with Windoze for a few more years :-)

---

### Post by dragonfly41 on 2011-04-25
I don't know if this will just muddy the waters but here is another link I found .

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by PM47 on 2011-05-07
After much wrangling as to which way to go I relented and installed Wine and Pegasus Mail. I installed Wine using the Synaptic package manager. I made a copy of my Pegasus mail folders on my NAS device (just in case), configured Wine with drive P:\ pointing to the new NAS mail folder (exactly as set up on my Windoze system), installed Pegasus Mail and manually set it up to use the existing mail folders on drive P:, rather than running the setup wizard. Amazingly it just works !!

I had one minor problem - I found Pegasus Mail Vn 4.61 wasn't reliable, I had a couple of program crashes so dropped back to Vn 4.41, which I've been using on Windoze for ages. I spent a couple of hours this afternoon sending test mails back and forth and so far it seems to be quite reliable. I shall run Pegasus in 'receive only' mode for a few days, in parallel with my Windoze system, before switching to using the live Pegasus folder on the NAS. If all is well I should now have access to my emails from either Windoze or Linux.

Hopefully that's another hurdle out of the way in my quest to escape from Windoze :-)

---

### Post by dragonfly41 on 2011-05-07
Long may Pegasus reign!

I haven't taken the plunge yet to run Pegasus in wine.

I've been trying Thunderbird in ubuntu.   

But I've got a legacy database in Pegasus so I might follow your lead.

---

### Post by PM47 on 2011-05-13
I'm still running 'read only' from my mail server, i.e. the mail isn't deleted from the server by Pegasus Mail. The only wrinkle so far is that Pegasus reads up to three copies of each mail from the server, which is a little annoying, but not a major problem. I'm hoping this problem will vanish when I allow Pegasus to delete the mail from the server. Otherwise everything appears to be Ok so far.

---

### Post by PM47 on 2011-05-15
Now running live. The repeated read problem has vanished. I can now manage my emails from any workstation using either windoze or linux as both use the same mail folders on my network storage device :-)

---

### Post by dragonfly41 on 2011-05-15
that's good to know .. with v4.41

however I've hit problems trying to install later versions v4.61 or v4.52

when I find time I'll try to find what is causing the installation error.

sometimes it just requires a *.dll to be added (I found this with another useful windows app - keynote).

---

### Post by PM47 on 2011-05-15
> **dragonfly41 said:**
> 

...however I've hit problems trying to install later versions v4.61 or v4.52...



I managed to install Vn 4.61 Ok, the only reasonI junked it was that it hung up a couple of times while I was using it. From the Pmail web site it looks like Vn4.61 is quite a major re-write, heading for releasing Vn5. Vn4.52 appears to be only a minor update on 4.41, if Iget a chance I'll try 4.52 and see what happens.

---

