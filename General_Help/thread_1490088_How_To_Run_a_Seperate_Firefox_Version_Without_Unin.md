---
title: "How To Run a Seperate Firefox Version Without Uninstalling The Old"
date: 2010-05-21
forum: General Help
---

### Post by tomcatjosh on 2010-05-21
Hey guys. I was wanting to run a nightly build of firefox. So i downloaded the tar file extracted and ran the firefox script. It went straight to my normal browser. Do you know how to make it go to the 3.7 Nightly without affecting the normal stable Build.
In case anyone was wondering, im trying to test WebM.

Thanks for any help!!
Josh

---

### Post by wojox on 2010-05-21
Extract it and move the folder to /opt

```
sudo mv firefox /opt
```

Then create a New Item in your Main Menu with the command

```
/opt/firefox/firefox
```

---

### Post by lovinglinux on 2010-05-21
Install [FoxTester](http://foxtester-extension.blogspot.com) extension. It allows you to check integrity of the downloaded file, install, launch and uninstall any number of Firefox versions without even closing your default Firefox.

The extension creates separate installation and profile folders for each version, so they don't interfere with your default installation/profile. Nevertheless, if you like a tested version, you can make it your default browser, so you can use it with your default profile and system integration. If you decide to revert to the default version, you can do it with a single click.

Everything is done from Firefox context menu. All you need is to configure a watched folder, where you will save all downloaded Firefox versions. Any firefox file saved on that folder will become available for installation automatically.

BTW, I'm the developer of that extension, so if you have any questions, feel free to ask here or in the [extension thread](http://ubuntuforums.org/showthread.php?p=9109976).

---

