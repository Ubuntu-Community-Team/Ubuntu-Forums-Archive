---
title: "Just starting"
date: 2006-05-05
forum: General Help
---

### Post by mafeishHASHISH on 2006-05-05
Hello everyone, I just started using Ubuntu, and I cant find out how to install LimeWire. I have the RPM file on my desktop and I can't install it for some reason. Can somebody walk me through the proccess please? 

Thank you, 

Omar McTabi.

Also : Is there anything adivse or anything that you would like to tell me using this new OS? It seems pretty simple to me, but just incase, please inform me.

---

### Post by rado_london on 2006-05-05
Hi. The RPM packages arent officially suported by ubunut. It uses DEB packages. However there is a workaround. Go to System-Administrator-Synaptic and enable all repositories. Then search for alien. Install it and the fire up Aplications-accesssories-terminal. Then type in:
```
sudo alien /the/path/to/the/rpmpackage/and/therpmpackage.rpm
```
The in the folder next to the rpm should be new DEB package. All you have to do is :
```
sudo dpkg -i packagenam.deb
```

GENERAL TIP: search the forums for Automatix. It will save you much headache with setting up multimedia codecs and flash etc.

Good luck

---

### Post by truthfatal on 2006-05-05
It would be much easier to install Limwire using a .deb package. RPMs are generally for RedHat based distros.

There's bound to be a .deb kicking around somewhere. If not, try looking in the Ubuntu Package manager (Add Applications in the Applications menu) for the RPM tools. or a tool to convert RPMs to DEBs.

If all else fails, get the "Other" version of Limewire (Choose "Other" OS when picking a download) you should get a .run file and a README tar.gz'd together. Untar and read the README then if all seems well, run ./LimeWireOther-[version].run in the terminal.

This advice comes straight from an over a year old memory... so take it perhaps with a grain of salt.

---

### Post by skippy81 on 2006-05-05
Hello mate, welcome to 'da linux :p .

Whilst you no-doubt could install limewire with a bit of effort - how about trying out a different client?  Linux has far more variety and quality in its file sharing applications than windows does IMO.   

gkt-gnutella is one of the best known Linux clients. Installing it is an absolute breeze - providing you have an internet connection up and running.  

1) Open the "synaptic package manager" under "system-admin" menu.

2) You need to enable the extra file repositories - multiverse and universe.

> 2.3. 	

How do I add Universe and Multiverse?
	

By default, Ubuntu comes pre-configured with basic and security update repositories. To enable the extra Universe and Multiverse repositories:

   1.

      Start Synaptic by selecting System->Administration->Synaptic Package Manager from the desktop menu system.
   2.

      In Synaptic choose Settings-> Repositories.
   3.

      Click the Settings button.
   4.

      Tick Show disabled software sources, then click Close.
   5.

      On the Repositories dialog box click Add. There are three separate repositories; Breezy Badger, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes.
   6.

      You should now see checkboxes next to each repository, scroll through the list and ensure they are all checked.


3) You now have access to tons of packages which install pretty much instantly. Have a search under "edit" for GKT-GNUTELLA, you never know you might find loads of stuff you like.

---

### Post by jtxx000 on 2006-05-05
Try installing frostwire.  It's pretty much a free version of frostwire pro.  sudo apt-get install frostwire

---

### Post by nursegirl on 2006-05-06
I echo rado_london in encouraging you to try [Automatix]("http://ubuntuforums.org/showthread.php?t=138405"). It includes frostwire, and a whole bunch of multimedia stuff. When you're first moving to Ubuntu, it can be hard because you don't know the names of the free programs that are equivalent to the programs you used with your previous OS. Automatix helps.

---

### Post by mafeishHASHISH on 2006-05-06
Hey I just want to Thank All of you! I got LimeWire running, and I am also running Automatix. It is really awesome, I don't know how to thank you, you really really helped me. Thanks. :D 

I know! I'll sing you a song! :-({|= :-({|=

---

### Post by rado_london on 2006-05-06
Thanks for the song mate!

---

