---
title: "Where Do I Look?  And Which One Is It?"
date: 2010-03-16
forum: General Help
---

### Post by DeadlyOats on 2010-03-16
I installed Vuze, formally "Azureus", from the downloaded .tar file.  It installed properly, and is running.  But its shortcut icon is not listed in the Applications Menu.  I want to add the shortcut icon to the Applications Menu.  But I don't know where the package installed.  I don't know where I need to browse for the program.

I right click on Applications, and click on "Edit Menus".  I then click on the "Internet" category, and then click on "+ New Item".  I get the "Create a Launcher" dialog box.  Next to the "Command" box is the browse button.  I don't know where to browse to find the path to Vuze, and thus add it to the "Applications" Menu.  Also, even if you tell me which folder to look in, I won't know which item to click on.  There may be several items with the word "Azureus" or "Vuze" in its name, and I won't know which one I need to select.

Help, please.

---

### Post by stoneage on 2010-03-16
If you built it from source try entering ```
whereis vuze
``` in a Terminal

If not the executable is in the Vuze folder that you extracted to.

If you download it from getdeb.net it will be easier to manage and update:-
[http://www.getdeb.net/software/Azureus](http://www.getdeb.net/software/Azureus)

---

### Post by n0dix on 2010-03-16
In console do: whereis vuze, or locate vuze.

---

### Post by 3rdalbum on 2010-03-16
> **DeadlyOats said:**
> Next to the "Command" box is the browse button.  I don't know where to browse to find the path to Vuze, and thus add it to the "Applications" Menu.  Also, even if you tell me which folder to look in, I won't know which item to click on.  There may be several items with the word "Azureus" or "Vuze" in its name, and I won't know which one I need to select.

Vuze is probably in /usr/bin or /usr/local/bin. It might possibly be in /opt.

If you can run it by typing its name into the terminal, then all you need to do is put "vuze" into the "Command" box.

Begs the question: If you don't know where it is, and there's no launcher for it, then how are you running it (you say it's running correctly)? I just assumed you were typing its name into the terminal.

---

### Post by DeadlyOats on 2010-03-16
Thanks, all for your replies.  I extracted the .tar file in the download folder, and double clicked on an icon.  It gave me the option to 'run in terminal', 'display', 'cancel', and 'run'.  I thought I was installing it when I chose to 'run in terminal'.  Vuze began running right away (what a fast install, I thought).  I now realize that when I extracted it, That _WAS_ the installation, and that running it in terminal, was *running* the app.  I realized this, because every time I closed the terminal, the app closed too.  So, when I chose to 'run' the app (not in terminal), the app opened and kept running.

I see now that what I need to to is extract the .tar file in a directory where programs need to be, and that will be the path for the launcher.

If my assumptions are wrong, please tell me.

I will delete the extracted Vuze folder in the downloads folder, and re-extract it in /usr/bin, per 3rdalbum, programs should be in /usr/bin, /usr/local/bin or in /opt.  I'll do it in /usr/bin.

Thanks for your help.  In the future, I'll know to use whereis <program name> or locate <program name> to search out the location of executable files.

Update:

I was unable to extract it in /usr/bin, /usr/local/bin, nor in /opt, because I don't have permissions.  So, I created a folder called programs in my Home folder, and did it there.  I successfully created the shortcut, but I could not find the little blue frog for the icon, so I'm using a game icon for it instead.

---

### Post by ndefontenay on 2010-03-16
Hi.

When you have finally extracted your vuze folder to /usr/bin you can create a shortcut on your desktop or wherever you want (task bar or menu). Right click on your desktop. Create new shortcut. In the Command field, type vuze. Choose a nice icon and drag it wherever you want when you're done with the configuration.

---

