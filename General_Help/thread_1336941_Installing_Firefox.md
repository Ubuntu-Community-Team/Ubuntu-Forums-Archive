---
title: "Installing Firefox"
date: 2009-11-25
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2009-11-25
I've had Ubuntu 9.04 installed in VirtualBox under Windows Vista for a few months, but haven't bothered with it much until now.  I downloaded Firefox 3.5.5 from the Mozilla website, and extracted it to the desktop with Archive Manager, but every time I run it, it asks me if I want to run of display its contents. After I click Run, it does load up and works fine, but how do I get rid of the message? Have I even installed Firefox right?

TIA

---

### Post by jacobs444 on 2009-11-25
the way I did it in jaunty was to use the package manager to uninstall all firefox packages, then open terminal and 
sudo cp -r /whereverfirefox3.5.5-folder-is /usr/share
then sudo ln -s /usr/share/firefox/firefox /usr/bin/firefox
then run firefox(you will have to set a custom icon though!
make a launcher which has the command firefox, and change the icon to one of the ones in /usr/share/firefox/icons

---

### Post by scouser73 on 2009-11-25
**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have firefox installed.

---

### Post by ..::| Dave89 |::.. on 2009-11-25
I went by [scouser73]("http://ubuntuforums.org/member.php?u=536148")'s instructions, works great, do I do this with other applications as well? What's the best way to uninstall Firefox 3.0.8?

---

### Post by jacobs444 on 2009-11-25
through the package manager, i think you can do it that way with other apps.

---

### Post by scouser73 on 2009-11-25
> **..::| Dave89 |::.. said:**
> I went by [scouser73]("http://ubuntuforums.org/member.php?u=536148")'s instructions, works great, do I do this with other applications as well? What's the best way to uninstall Firefox 3.0.8?

Hi Dave, to uninstall previous versions of Firefox, go to **System > Administration > Synaptic Package Manager** and search for Firefox.  You will be presented with a few entries relating to Firefox, right click on each and select **Mark For Complete Removal** then click **Apply** & **Apply** again.

At this point I would lock those packages of Firefox from updating, so highlight the ones you've just removed and select **Package** & check the box [B]Lock Version
[/B]
You will now only have the version of Firefox that you've installed.

You can do that with other applications but if you can find an easier alternative such as installing a **.deb** file or using **Synaptic Package Manager** then I would go with that, unless of course you wish to have the latest releases of a program.

---

### Post by ..::| Dave89 |::.. on 2009-11-25
I've removed all trace of Firefox 3.0.8. Thanks for your help. Now I'm going to continue exploring around Ubuntu! I like what I've seen so far.

---

### Post by Nottawa on 2009-11-26
I followed Scouser's directions and all went well except that nothing happens when I try to start my new version of Firefox.  How do I fix this?

---

