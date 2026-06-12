---
title: "Changing boot order"
date: 2011-03-30
forum: General Help
---

### Post by orrymr on 2011-03-30
Hi guys,
I'm dual booting ubuntu and win7, but when I start my pc Win7 is by default the OS that gets loaded if I don't hit the down arrow and press enter. How do I change this so that Ubuntu is my defualt?

Thanks.

---

### Post by drs305 on 2011-03-30
If you like GUI apps, try Grub Customizer.

If you would prefer to edit the Grub2 configuration files, you can do that as well.

Take a look at the "Customizer" (GUI) and "Tasks" (see Item #2 in that link) links in my signature line.

---

### Post by orrymr on 2011-03-30
Is there any reason other than ease of use to use the GUI over editing the files manually?

---

### Post by orrymr on 2011-03-30
Ok, well I edited /etc/default/grub, and changed to
```

DEFAULT = 1

```
which worked as expected; changing the default to the second option. The problem is, that Windows boot loader runs before Grub opens. So the default for that boot loader is Windows 7. Only after I've chosen Ubuntu in the Windows 7 boot loader do I get taken to Grub. From there I have the option of logging into Ubuntu (normal or recovery) or going back to Win7 Loader. Any ideas on how to disable Windows 7 boot loader?

---

### Post by drs305 on 2011-03-30
> **orrymr said:**
> Is there any reason other than ease of use to use the GUI over editing the files manually?

You mean besides saving time and not having to tear your hair out? 8-[8-[

Seriously, even though I wrote the thread on using Grub Customizer, I have not experimented with it enough to tell if it has additional features or is more robust than the original G2 files. I would suspect not, but I don't want to rule out the possibility that Daniel Richter has done so.

Personally I like changing the files manually, but I know fairly well how Grub2 works. 

One thing I haven't grown comfortable with in Grub Customizer, as much as I think it is a great app for most users, is that it creates additional files, modifies them, and stores the originals away. So the files running Grub2 are not the ones I'm used to. But if you don't ever look at the files the contents don't really matter as long as the result match your expectations. Many, if not most, users have no need to view the actual files as long as they get the job done.

Added: Saw your latest post after writing the above. Sounds like you are using WUBI (Ubuntu inside Windows). Since Wubi is just a file within Windows, you need to go through Windows to get to it. I think you could change which one is the default (Windows or Ubuntu) [s]but think that if you use the default Windows bootloader you are going to have to live with it[/s] (*see bcbc's post below*) or use another Windows loader. Many users try out Ubuntu with Wubi and then migrate Ubuntu to its own partition. At that point, you can use Grub as your bootloader and have a one-selection boot process.

---

### Post by Karlchen on 2011-03-30
Hello, orrymr.
> I'm dual booting ubuntu and win7, but when I start my pc Win7 is by default the OS that gets loaded if I don't hit the down arrow and press enter. How do I change this so that Ubuntu is my defualt?In order to change default OS which the Windows 7 bootloader will use, you will either have to use the Windows 7 commandline programme **bcedit** or you might like to use graphical version of **bcedit**:**[EasyBCD 2.0.2]("http://neosmart.net/dl.php?id=1") **instead.
Reason:
On Windows 7 there is no more pure ANSI file boot.ini which you can edit manually using your favourite text editor. Instead Windows reads a binary boot configuration file which can be viewed and modified by using either **bcedit** or **EasyBCD**.

HTH,
Karl

---

### Post by bcbc on 2011-03-30
You can change the default OS as follows: right click on Computer, Properties, Advanced system settings, Startup & Recovery settings, change default from drop down box. Do NOT set the timeout to zero or Windows will not boot anymore.

---

### Post by drs305 on 2011-03-30
> **bcbc said:**
> You can change the default OS as follows: right click on Computer, Properties, Advanced system settings, Startup & Recovery settings, change default from drop down box. Do NOT set the timeout to zero or Windows will not boot anymore.

Good to know, even if I don't use Windows. Does this apply only to Win7? If not, how far back does it go?

---

### Post by bcbc on 2011-03-30
> **drs305 said:**
> Good to know, even if I don't use Windows. Does this apply only to Win7? If not, how far back does it go?

Apart from some minor stuff (like "Computer" being "My Computer") this works the same on XP (service pack 3). I can't vouch for every release/service pack but I guess they're all the same.

The main difference between XP and Vista/7 is that on XP you could modify the boot.ini by hand, whereas with Vista/7 it's no longer possible with the BCD. So things like setting the timeout to zero are infinitely harder to fix on Vista/7. And manually adding or removing boot entries has to be done with bcdedit.exe or easyBCD.

---

### Post by idoitprone on 2011-03-30
why dont you change the order in which grub find each entry. Go to /etc/grub.d/. For grub, "os_prober" is the file that find windows, while file named "linux" finds linux partition obviously. Notice the numbers in front of the name. It is the order in which grub finds each os. Just change the number for os prober before linux and after the debian number.

turn 30_os-prober to something like 06_os-prober. 

Be careful, damaging these scripts may render certain operating system unable to boot.

---

### Post by drs305 on 2011-03-30
> **idoitprone said:**
> why dont you change the order in which grub find each entry. 

I believe the discussion has evolved now into the boot order in the Windows bootloader and not in the Grub2 display. 

Your method *would* work to change the display order (and boot order if the DEFAULT= number wasn't changed) if the OP wanted to see the Windows OS listed first in Grub2.

---

### Post by Karlchen on 2011-03-31
> **bcbc said:**
> You can change the default OS as follows: right click on Computer, Properties, Advanced system settings, Startup & Recovery settings, change default from drop down box. Do NOT set the timeout to zero or Windows will not boot anymore.Confirmed. Same on Windows 7. - Oh well, there are a few things which Windows can do out of the box without using third party tools. Seems as if I have started forgetting this. :oops:
So it is pretty trivial to instruct the Windows boot loader to boot Ubuntu by default. - And if it is a Wubi installation like on my machine, then you will have to tell the Windows boot loader, not Grub.

Karl

---

