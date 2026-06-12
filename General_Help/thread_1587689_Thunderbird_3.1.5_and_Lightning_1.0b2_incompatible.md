---
title: "Thunderbird 3.1.5 and Lightning 1.0b2 incompatible"
date: 2010-10-04
forum: General Help
---

### Post by Ralph L on 2010-10-04
I am running lucid with Thunderbird 3.1.5 (32 bit) and trying to install Lightning 1.0b2.  Whenever, I install Lightning, I cannot restart TB, if I drop it.  No error message.  I have to start TB from the Terminal with "thunderbird -safe-mode", remove Lightning, and then everything works.  I read of others having problems with TB and Lightning, but most of these are 64 bit.  I am 32 bit.  Please note that I have removed all other extensions from TB, but I still can't run Lightning.

One concern I have is that even though Synaptic says that TB 3.1.5 is install, the Help>About says just TB 3.1.  It doesn't include the ".5".  I am concerned that despite what Synaptic says, I might not have version 3.1.5 installed.  Is there any way to check if I really have version 3.1.5 installed?

I tried to install the latest nightly build of Lightning, but I got the error message "Lightning 1.0b3pre could not be installed because it is not compatible with Firefox 3.6.10".

Does anybody have any other suggestions of how to get Lightning to run with Thunderbird??

Ralph

---

### Post by HereInOz on 2010-10-04
This is not going to be much help, but I eventually gave up on the Thunderbird / Lightning runaround with upgrades, and moved over to Evolution.  Thunderbird is still my favourite, but I got tired of chasing the Lightning issue all the time, as I need a reliable calendar.

You can import all your Thunderbird mail and Lightning appointments into Evolution and because it is an integrated application, it doesn't break (often) on upgrades.

Sorry I can't be of more use.

---

### Post by pushpsmarty on 2010-10-04
[SIZE=2][COLOR=Black]This is the problem-
I am unable to install gnochm.
I know i have some alternatives fo chm viewer but i want to know in detail why it is not installing. Which currently installed package is interrupting.

This the screenshot->

pushpi@Revolution:~$ sudo apt-get install gnochm
[sudo] password for pushpi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnochm: Depends: python-gtkhtml2 but it is not installable
E: Broken packages

Thanks in advance.....!
---Pushpi
[/COLOR][/SIZE]

---

### Post by nosmokenofire on 2010-10-04
Hi Ralph,

Yesterday I posted how I got around this problem in this thread: [http://ubuntuforums.org/showthread.php?t=1463762&page=11](http://ubuntuforums.org/showthread.php?t=1463762&page=11) (last post)

It works fine.

All the best.

---

### Post by Ralph L on 2010-10-04
nosmokenfire

Thank you very much for your help.  I will give that a try.  To do so I think I need to back off from TB 3.1.5 to 3.1.4 or earlier.

Thanks again

Ralph

---

### Post by nosmokenofire on 2010-10-06
Hi Ralph,

I think that if you follow the installation instructions then you will end up with the latest stable mozilla build version which appears to be 3.1.4. As I understand it, after that the updates come through the Ubuntu software centre.

I'm really not that much of a computer genius, but I managed to get it all set up alright, so it is pretty easy...

All the best.

---

### Post by Ralph L on 2010-10-11
The scenario I gave below does NOT work. For some reason when TB is installed using sudo, it is only accessible by using sudo. So don't do what I did.  Also I still had to back out Lightning using the "sudo thunderbird -safe-mode" command.


I installed TB 3.1.4 and Lightning 1.0b2 and everything seemed ok.  I haven't used the calendar yet, so I don't know if any problems exist there.

I did the install as follows:

1.  Brought up Terminal and entered "sudo thunderbird"
2.  Once TB came up I went to the TB menu>Help>Check for Updates.  3.1.4 was the latest stable version so I installed it.  No problem.
3.  Went to TB menu>Tools>Addons and found Lightning 1.0b2 and installed it.

Ralph

---

### Post by Hilko on 2010-10-14
Hi, I use 64bit Ubuntu. In the Software Centre I can find the lightning extension for Thunderbird, but, there is no install button! I cannot install it! I can click on more info, and it shows me a screenshot and a short description and that's all.

Another strange thing is that when I search for add-ons from within Thunderbird it does not find the lightning extension.

Can anyone explain this? Does anyone have a the same problem?

---

### Post by perspectoff on 2010-10-14
Yeah, I had the same problem.

I am using Sunbird as a standalone app, instead of the Lightning extension for Thunderbird.

I have no problems with Sunbird (64-bit or 32-bit).

wget -O sunbird-current.tar.bz2 [http://download.mozilla.org/?product=sunbird-1.0b1&os=linux64&lang=en-US](http://download.mozilla.org/?product=sunbird-1.0b1&os=linux64&lang=en-US)
tar -xvjf sunbird-current.tar.bz2

I happen to like to keep Sunbird in an /etc/sunbird directory, so I copy the extracted files there.

I then just create a menu item for /etc/sunbird/sunbird

Works great. I happen to like to use Sunbird with the DAViCal group calendar server, but it works with any CalDAV or iCal server.

It is, of course, pretty much the same code as Lightning.

---

### Post by Hilko on 2010-10-14
Thanks for your reply. I forgot to say; Sunbird has the same strange problem. I find it in the software centre, but there is no install button! Why show something I cannot install ?

Btw: I still have Sunbird installed in an older Ubuntu install, so I know it was possible before. I know I can download it from the mozilla site, but I prefer installing from the repos. Furthermore, the support for sunbird is gonna end soon, see [http://www.mozilla.org/projects/calendar/](http://www.mozilla.org/projects/calendar/) .

---

### Post by proycon on 2010-10-17
On 64bit maverick, download and install these in thunderbird, works for me:

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/)

---

