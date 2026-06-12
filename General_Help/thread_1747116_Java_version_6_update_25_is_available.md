---
title: "Java version 6 update 25 is available"
date: 2011-05-02
forum: General Help
---

### Post by Cavsfan on 2011-05-02
I just installed the 64 bit version of Java 6.25.
The instructions for checking your version and installing the latest are in my signature.

I installed the 64 bit version myself. Just be aware that the instructions are for update 24 and you will need to change this to 25 where necessary.
The instructions for 32 bit Java are on the left and 64 bit Java are on the right side in the link.

I had version 6 update 20 and the PPA installed to update it manually but, it did not update.
Might be early I am not sure when 25 came out, any way I like the manual way.

---

### Post by boblizar on 2011-05-11
i used your update method and it works well...  however i changed some things around.  i used oracle java jdk 4 64 ubuntu 11.04....

```
sudo ln -s /usr/lib/jdk1.6.0_25/ /usr/lib/java

sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/java/bin/java" 1

sudo update-alternatives --set java /usr/lib/java/bin/java

ln -s /usr/lib/java/jre/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```

this is a more appropriate location for the JDK and usually the /usr/lib/java is a symlink pointing to the /usr/lib/jdk-version directory however i just dumped the 6.25 to the directory....  the symlink is more appropriate as you can delete the old jdk and drop the new jdk and symlink against the new jdk....

[http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u25-download-346242.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u25-download-346242.html) is the oracle JDK download link i used

not trying to steal your thunder, but rather trying to make your thunder branch further and zap more stuff =)  this is generally a distro agnostic solution, and it comes from my use of linux from scratch with out any package management.

---

### Post by Cavsfan on 2011-05-14
I just found that web page and it has been useful to me.
Glad to see an addition.
Thanks boblizar!

---

### Post by boblizar on 2011-05-16
no problem, thanks for the original posting....  its nice to do it the way ive done it.  i eventually deleted ubuntu and reinstalled, and symlinked instead of dropped to the directory.  as said before my links are distro agnostic.  your "update-alternatives" commands are ubuntu specific (and i imagine they are generic debian commands)

instead of chmod +x jdk.....

```
sh jdk-6u25-linux-x64.bin
```

testing has shown this solution to include firefox/seamonkey/chromium to be updated.  not so sure about konqueror.  i run a virtual box VM for safari IE8 testing also.  web pages i make get tested for firefox/seamonkey/chrome/safari/ie8/konqueror...  i have a gauntlet of browsers =D

---

### Post by mons00n on 2011-05-26
worked great thanks guys!

---

### Post by Cavsfan on 2011-05-27
> **mons00n said:**
> worked great thanks guys!

You are welcome! Nice avatar! :)

---

### Post by DinoT1985 on 2011-05-27
> **boblizar said:**
> i used your update method and it works well...  however i changed some things around.  i used oracle java jdk 4 64 ubuntu 11.04....

```
sudo ln -s /usr/lib/jdk1.6.0_25/ /usr/lib/java

sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/java/bin/java" 1

sudo update-alternatives --set java /usr/lib/java/bin/java

ln -s /usr/lib/java/jre/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```this is a more appropriate location for the JDK and usually the /usr/lib/java is a symlink pointing to the /usr/lib/jdk-version directory however i just dumped the 6.25 to the directory....  the symlink is more appropriate as you can delete the old jdk and drop the new jdk and symlink against the new jdk....

[http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u25-download-346242.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u25-download-346242.html) is the oracle JDK download link i used

not trying to steal your thunder, but rather trying to make your thunder branch further and zap more stuff =)  this is generally a distro agnostic solution, and it comes from my use of linux from scratch with out any package management.

ok thats confused me. which parts do I replace with these? whats the difference between java versions?

---

### Post by boblizar on 2011-10-13
[http://ubuntuforums.org/showthread.php?t=1859354](http://ubuntuforums.org/showthread.php?t=1859354)

for java 1.7  i have re-written this from scratch  many thanks to the original poster, i could not of done it with out u!  (i dont understand the ubuntu specific codes to replace java)

VV this is my masters thesis VV
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)

---

### Post by Cavsfan on 2011-10-18
Update 29 is now available.

---

### Post by Catbells on 2011-10-29
Your tutorial was great Cavsfan.  I don't think the information is anywhere else so it was great to have it.

For users who, like me, prefer graphics and windows to the terminal, let me just describe a superficially different method from steps 1-6 on Cavsfan's web page.  I'm not a specialist in user guides.  Please accept my apologies if my instructions are talking down to you or if they aren't easy to understand.

1. Download the jre file as Cavsfan describes on his web page. You can get to it from the green hyperlink in any of his posts.
2. Open Nautilus and navigate to the Download folder.  Right-click on the file and choose Properties from the pop-up menu. Click the Permissions tab.  Between "Execute:  " and "Allow executing file as program" is a little square box.  Click it and you will see an X appear in it.  Click the Close button.
3. Press Alt+F2.  A dialogue box appears.  Near the top, type or copy & paste: -
[COLOR=Blue]gksudo nautilus[/COLOR]
Nautilus opens in a window where you are Root user.
4. Navigate to File System then to the opt folder.  Inside opt, find the Java folder.  If it's not there, create it.  Inside the Java create a subfolder called 32.  It's location is /opt/java/32.
5.  Open Nautilus in your usual way and navigate to the Downloads folder where you will find the jre file you downloaded in step 1.  Drag this file to /opt/java/32.
6.  Go back to Cavsfan's web page and follow his guide from 7 onwards.

---

### Post by Cavsfan on 2011-11-01
> **Catbells said:**
> Your tutorial was great Cavsfan.  I don't think the information is anywhere else so it was great to have it.

For users who, like me, prefer graphics and windows to the terminal, let me just describe a superficially different method from steps 1-6 on Cavsfan's web page.  I'm not a specialist in user guides.  Please accept my apologies if my instructions are talking down to you or if they aren't easy to understand.

1. Download the jre file as Cavsfan describes on his web page. You can get to it from the green hyperlink in any of his posts.
2. Open Nautilus and navigate to the Download folder.  Right-click on the file and choose Properties from the pop-up menu. Click the Permissions tab.  Between "Execute:  " and "Allow executing file as program" is a little square box.  Click it and you will see an X appear in it.  Click the Close button.
3. Press Alt+F2.  A dialogue box appears.  Near the top, type or copy & paste: -
[COLOR=Blue]gksudo nautilus[/COLOR]
Nautilus opens in a window where you are Root user.
4. Navigate to File System then to the opt folder.  Inside opt, find the Java folder.  If it's not there, create it.  Inside the Java create a subfolder called 32.  It's location is /opt/java/32.
5.  Open Nautilus in your usual way and navigate to the Downloads folder where you will find the jre file you downloaded in step 1.  Drag this file to /opt/java/32.
6.  Go back to Cavsfan's web page and follow his guide from 7 onwards.


Thanks. Another way to open a directory in Nautilus with root privileges is to set it up in Ubuntu Tweak. If you don't already have it, it's in the repositories.
Just open up SPM (Synaptic Package Manager) and install it from there.
Then open it (Applications > System Tools > Ubuntu Tweak) and on left toward the bottom is **Nautilus Settings**.
Click on that and put a check in **Open folder with root privileges** and then close Ubuntu Tweak.
It should ask for your password.
Then when you go to any folder just right click on that folder, there will be an option near the bottom to **Open as Administrator**.

That is how you use the GUI version versus entering [color=blue]gksudo nautilus[/COLOR] every time you need root privileges.

You did realize that update 29 is the latest, right?

This thread I started on May 2nd for version 25 sure got the attention.

---

