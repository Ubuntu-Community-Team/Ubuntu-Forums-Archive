---
title: "Firefox won't start!!!"
date: 2009-07-14
forum: General Help
---

### Post by FastMady123 on 2009-07-14
Firefox won't start. I was installing themes and it was working at that time. Then, I uninstalled a theme and restarted the computer, I log in and clicked on the Firefox icon, it will not load. I typed "firefox" into the command and it still will not load. I try to delete the Firefox profile and I got an error message that Firefox is working but not loading. I restore the profile and I still have that error. I restated the computer and still that same error. I may try to copy the profile to another user acccount and/or file a bug report. What should I do to fix this problem?

---

### Post by lovinglinux on 2009-07-14
Go to "System >> Administration >> System Monitor" , then kill all firefox processes.

Then open ~/.mozilla/firefox/ and move your profile somewhere else.

If you are using Firefox 3.5 from the repos, then your profile will be under ~/.mozilla/firefox-3.5.

This should fix it. If not, then repeat the process, but add the steps below before starting Firefox:

Then go to "System >> Administration >> Synaptic Package Manager", search for Firefox, then mark *firefox* and *firefox 3.0* for re-installation. Also mark *firefox-3.5* if you are using Shiretoko. Click apply. Start Firefox from terminal and check if you get any errors.

---

### Post by s.fox on 2009-07-14
Hi,

When you tried to run it from terminal you said it wouldn't load.  What error message(s) displayed?

Thanks,

-Silver Fox

---

### Post by FastMady123 on 2009-07-14
When I typed "firefox", it did not show an error message.

---

### Post by JB2009 on 2009-07-15
I have the same situation. I have a clean installation of UB9.04, plus all updates, plus FPC, plus Lazarus, plus Meld. After that Firefox does nothing when run from an icon, and no error message when run from the terminal.

The "~/.mozilla/" folder is completely empty - probably because Firefox has never run successfully.

Could this be a bug introduced by a recent OS update? I installed three copies of UB9.04 yesterday (including two onto different partitions of the same machine that doesn't work now) with no problems.

JB.

Edit: I've just found that "sudo firefox" DOES work (though probably a bad idea...)

---

### Post by lovinglinux on 2009-07-15
> **JB2009 said:**
> I have the same situation. I have a clean installation of UB9.04, plus all updates, plus FPC, plus Lazarus, plus Meld. After that Firefox does nothing when run from an icon, and no error message when run from the terminal.

The "~/.mozilla/" folder is completely empty - probably because Firefox has never run successfully.

Could this be a bug introduced by a recent OS update? I installed three copies of UB9.04 yesterday (including two onto different partitions of the same machine that doesn't work now) with no problems.

JB.

Try this in terminal:

```
sudo chown -R $USER:$USER ~/.mozilla
firefox -P
```

It should start the Firefox Profile Manager and default profile should be created. Start it and see how it goes.

From: **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

### Post by nikhilbhardwaj on 2009-07-15
delete the .mozilla directory in your home partition
dont worry it'll be recreated when you start firefox again
that should fix it

---

### Post by lovinglinux on 2009-07-15
> **nikhilbhardwaj said:**
> delete the .mozilla directory in your home partition
dont worry it'll be recreated when you start firefox again
that should fix it

Please see note below:

> **[color=#CC0000]Note:[/color]** Several posts on these forums recommends moving, renaming or deleting **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder to solve Firefox issues. While this will certainly remove any corrupted Firefox profiles and thus solve many common issues, you should consider that the **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder is also the place where other Mozilla applications might store their profiles (Sunbird, etc), so removing this folder will also remove their settings. 

Firefox profiles are stored under **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** folders, where **[COLOR="Sienna"]x.y[/COLOR]** is the Firefox version. So if you need to remove a Firefox profile to fix a problem, then remove **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** not **[COLOR="Sienna"]~/.mozilla[/COLOR]**. 

Nevertheless, there also no reason to delete the entire profile if you can pinpoint the culprit inside it. Most common Firefox issues can be traced back to a single profile file. So, if you can avoid removing the entire profile, you wil be able to preserve other settings like extensions, themes, bookmarks, cookies and passwords.

---

### Post by JB2009 on 2009-07-15
> **lovinglinux said:**
> Try this in terminal:

```
sudo chown -R $USER:$USER ~/.mozilla
firefox -P
```

It should start the Firefox Profile Manager and default profile should be created. Start it and see how it goes.

From: **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).
Yes thanks - that has fixed the problem. 

Much appreciated.

JB.

---

### Post by lovinglinux on 2009-07-15
> **JB2009 said:**
> Yes thanks - that has fixed the problem. 

Much appreciated.

JB.

You are welcome.

---

