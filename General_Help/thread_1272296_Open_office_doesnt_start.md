---
title: "Open office doesnt start"
date: 2009-09-22
forum: General Help
---

### Post by handyguy on 2009-09-22
Hello currently i am using ubuntu 9.04 and open office 3. Recently i tried to install a grammar extension for writer and boom open office crashes. Now it doesnt start and i really need it to do homework for my AP euro please help. When i put ooffice -writer in terminal nothing happens. Also even the other openoffice applications dont start any help would be appreciated. Thanks in advance.

---

### Post by oboedad55 on 2009-09-22
> **handyguy said:**
> Hello currently i am using ubuntu 9.04 and open office 3. Recently i tried to install a grammar extension for writer and boom open office crashes. Now it doesnt start and i really need it to do homework for my AP euro please help. When i put ooffice -writer in terminal nothing happens. Also even the other openoffice applications dont start any help would be appreciated. Thanks in advance.

I had this problem once. Try dragging your /home/user/.openoffice folder out on to the desktop. You'll lost any customization you had but that's no big deal. If it works delete the .openoffice folder.

---

### Post by handyguy on 2009-09-22
> **oboedad55 said:**
> I had this problem once. Try dragging your /home/user/.openoffice folder out on to the desktop. You'll lost any customization you had but that's no big deal. If it works delete the .openoffice folder.

I just did this and then i opened open office and it created a new .openoffice folder but didnt start open office up now in the folder it goes 
/home/user/.openoffice.org/3/user/config and has an xml file in it

---

### Post by oboedad55 on 2009-09-22
> **handyguy said:**
> I just did this and then i opened open office and it created a new .openoffice folder but didnt start open office up now in the folder it goes 
/home/user/.openoffice.org/3/user/config and has an xml file in it

Remove it again and run from a terminal, "openoffice.org" and see if you get any error messages.

---

### Post by handyguy on 2009-09-22
> **oboedad55 said:**
> Remove it again and run from a terminal, "openoffice.org" and see if you get any error messages.
Nope same effect the terminal still shows nothing which seems odd to me but i opened the xml file and it says

```
<!--This is a generated file. Do not alter this file!-->
&#8722;
<java>
<enabled xsi:nil="true"/>
<userClassPath xsi:nil="true"/>
<vmParameters xsi:nil="true"/>
<jreLocations xsi:nil="true"/>
&#8722;
<javaInfo xsi:nil="false" vendorUpdate="2004-01-30" autoSelect="true">
<vendor>Sun Microsystems Inc.</vendor>
<location>file:///usr/lib/jvm/java-6-openjdk/jre</location>
<version>1.6.0_0</version>
<features>1</features>
<requirements>1</requirements>
&#8722;
<vendorData>
660069006C0065003A002F002F002F007500730072002F006C00690062002F006A0076006D002F006A006100760061002D0036002D006F00700065006E006A0064006B002F006A00720065002F006C00690062002F0069003300380036002F0063006C00690065006E0074002F006C00690062006A0076006D002E0073006F000A002F007500730072002F006C00690062002F006A0076006D002F006A006100760061002D0036002D006F00700065006E006A0064006B002F006A00720065002F006C00690062002F0069003300380036002F0063006C00690065006E0074003A002F007500730072002F006C00690062002F006A0076006D002F006A006100760061002D0036002D006F00700065006E006A0064006B002F006A00720065002F006C00690062002F0069003300380036002F006E00610074006900760065005F0074006800720065006100640073003A002F007500730072002F006C00690062002F006A0076006D002F006A006100760061002D0036002D006F00700065006E006A0064006B002F006A00720065002F006C00690062002F0069003300380036000A00
</vendorData>
</javaInfo>
</java>
```

---

### Post by oboedad55 on 2009-09-22
> **handyguy said:**
> Nope same effect the terminal still shows nothing which seems odd to me but i opened the xml file and it says

```
<!--This is a generated file. Do not alter this file!-->
&#8722;
<java>
<enabled xsi:nil="true"/>
<userClassPath xsi:nil="true"/>
<vmParameters xsi:nil="true"/>
<jreLocations xsi:nil="true"/>
&#8722;
<javaInfo xsi:nil="false" vendorUpdate="2004-01-30" autoSelect="true">
<vendor>Sun Microsystems Inc.</vendor>
<location>file:///usr/lib/jvm/java-6-openjdk/jre</location>
<version>1.6.0_0</version>
<features>1</features>
<requirements>1</requirements>
&#8722;
<vendorData>
660069006C0065003A002F002F002F007500730072002F006C00690062002F006A0076006D002F006A006100760061002D0036002D006F00700065006E006A0064006B002F006A00720065002F006C00690062002F0069003300380036002F0063006C00690065006E0074002F006C00690062006A0076006D002E0073006F000A002F007500730072002F006C00690062002F006A0076006D002F006A006100760061002D0036002D006F00700065006E006A0064006B002F006A00720065002F006C00690062002F0069003300380036002F0063006C00690065006E0074003A002F007500730072002F006C00690062002F006A0076006D002F006A006100760061002D0036002D006F00700065006E006A0064006B002F006A00720065002F006C00690062002F0069003300380036002F006E00610074006900760065005F0074006800720065006100640073003A002F007500730072002F006C00690062002F006A0076006D002F006A006100760061002D0036002D006F00700065006E006A0064006B002F006A00720065002F006C00690062002F0069003300380036000A00
</vendorData>
</javaInfo>
</java>
```

That's the java settings file. I've got one called "javasettings_Linux_x86.xml". You have the same one? You're completely deleting the /.openoffice.org file? What happens from the terminal? Any messages? Did this program work in the past? If so, do you remember changing, installing, anything?

---

### Post by handyguy on 2009-09-22
> **oboedad55 said:**
> That's the java settings file. I've got one called "javasettings_Linux_x86.xml". You have the same one? You're completely deleting the /.openoffice.org file? What happens from the terminal? Any messages? Did this program work in the past? If so, do you remember changing, installing, anything?

Yes i completely deleted everything but i just tried to install an open office writer extension then it crashed 15 minutes ago. I restarted and then posted and tried your instructions. Nothing happens in the terminal it just stays blank like its running the program but doesnt do user@user thing just stays blank with the cursor thing flashing. I will check this post tommorow because it is time for me to go to bed right now for school

---

### Post by oboedad55 on 2009-09-22
> **handyguy said:**
> Yes i completely deleted everything but i just tried to install an open office writer extension then it crashed 15 minutes ago. I restarted and then posted and tried your instructions. Nothing happens in the terminal it just stays blank like its running the program but doesnt do user@user thing just stays blank with the cursor thing flashing. I will check this post tommorow because it is time for me to go to bed right now for school

Okay, I just got my internet connection back. It's been raining here in Atlanta... Anyway, on other idea. I've had what you describe happen to me to with installing an extension like that. The next thing to try is to go into Synaptic and remove completely openoffice, including config files. Then make sure you've gotten rid of your .oppenoffice.org file, and all of that. Then re-install it and don't try the extension.

---

### Post by sjd on 2009-09-22
I found this solution[link]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=22726") and it solved the problem for me although I'm not sure why (or for how long?)


I am having the same problem, with a twist.  I removed the Ubuntu OO program because I have to save a lot of documents in Word format and since the 9/4/09 update the formatting has gotten wacky as well as the display.  I installed the Sun version using the instructions here (edited for OO 3.1.1.9) [http://hydtech.wordpress.com/2009/02/24/how-to-fresh-install-openoffice-301-on-ubuntu-810-intrepid/]("http://hydtech.wordpress.com/2009/02/24/how-to-fresh-install-openoffice-301-on-ubuntu-810-intrepid/")

No errors on install and icons for all programs in the menu.  The programs appear in Synaptic as Installed (local or obsolete)

On startup indicates the doc recovery msg and send options and crashes

I noticed Sun's UNO rt environ and the Gnome version, so I tried removing the Gnome version

Tried moving .openoffice.org dirs (had a v2 one to) the desktop, restarted, same crash

Starting via the terminal
The program 'openoffice.org' is currently not installed.  You can install it by typing:
sudo apt-get install openoffice.org-common
bash: openoffice.org: command not found

I have not done that as I believe that would try to install from the launchpad OO Jaunty version repos (which I removed)

Will keep looking for answers, but thought I'd start here.  Thanks!

---

### Post by handyguy on 2009-09-22
> **sjd said:**
> I found this solution[link]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=22726") and it solved the problem for me although I'm not sure why (or for how long?)


I am having the same problem, with a twist.  I removed the Ubuntu OO program because I have to save a lot of documents in Word format and since the 9/4/09 update the formatting has gotten wacky as well as the display.  I installed the Sun version using the instructions here (edited for OO 3.1.1.9) [http://hydtech.wordpress.com/2009/02/24/how-to-fresh-install-openoffice-301-on-ubuntu-810-intrepid/]("http://hydtech.wordpress.com/2009/02/24/how-to-fresh-install-openoffice-301-on-ubuntu-810-intrepid/")

No errors on install and icons for all programs in the menu.  The programs appear in Synaptic as Installed (local or obsolete)

On startup indicates the doc recovery msg and send options and crashes

I noticed Sun's UNO rt environ and the Gnome version, so I tried removing the Gnome version

Tried moving .openoffice.org dirs (had a v2 one to) the desktop, restarted, same crash

Starting via the terminal
The program 'openoffice.org' is currently not installed.  You can install it by typing:
sudo apt-get install openoffice.org-common
bash: openoffice.org: command not found

I have not done that as I believe that would try to install from the launchpad OO Jaunty version repos (which I removed)

Will keep looking for answers, but thought I'd start here.  Thanks!

thanks for the help it worked somehow.

---

### Post by oboedad55 on 2009-09-22
> **handyguy said:**
> thanks for the help it worked somehow.

Well, I'm not sure what helped but I'm glad it's working. I didn't realize you were not using the version for the repos. I should have thought to ask... Come back if you need more help.

---

