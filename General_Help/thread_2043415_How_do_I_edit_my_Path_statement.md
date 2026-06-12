---
title: "How do I edit my Path statement?"
date: 2012-08-16
forum: General Help
---

### Post by p3aul on 2012-08-16
I wanted to creata qtproject in netbeans 7.2 I have already installed the Qt sdk and know that it works. When Netbeans went to run Qt Designer it said it wasn't installed or hadn't been added to the path. I know Qt designer was installed cause I had just played around with it. That leaves the Path Statement which I don't know how to alter. The Which command says nothing when I try to locate Qt. it's not in user/bin/ either.
Thanks,
Paul

---

### Post by papibe on 2012-08-16
Hi p3aul.

You can modify your PATH in your ~/.bashrc for personal use, or set it globally at /etc/environment.

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1984328").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by p3aul on 2012-08-16
Well I found the environment file but I still don't know where the Qt install put Qt sdk or the Qt designer files that Netbeans wants :(
Thanks,
Paul

---

### Post by papibe on 2012-08-16
If you know the name of the package you installed, you can list all the content using 'dpkg'.

For instance, let's say I want to see everything on the package transmission-daemon:
```
dpkg -L transmission-daemon
```
The result will be:
```
/.
/var
/var/lib
/var/lib/transmission-daemon
/var/lib/transmission-daemon/downloads
/var/lib/transmission-daemon/info
/usr
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/transmission-daemon.1.gz
/usr/share/doc
/usr/bin
/usr/bin/transmission-daemon
/etc
/etc/default
/etc/default/transmission-daemon
/etc/init.d
/etc/init.d/transmission-daemon
/etc/transmission-daemon
/etc/transmission-daemon/README.json
/etc/transmission-daemon/settings.json
/var/lib/transmission-daemon/info/settings.json
/usr/share/doc/transmission-daemon

```
Regards.

---

### Post by p3aul on 2012-08-16
It wasn't installed from a deb package. was a binary. What they called an online install, I guess because it accessed the internet during the install. Qt Designer worked perfectly from what I could tell. You have to use too much coding in qt to suit me. I was hoping it would be more like Netbeans Java if run from Netbeans.

The file I installed from was:
 tSdk-online-linux-x86_64-v1.2.1.run

---

### Post by spjackson on 2012-08-16
The installer prompts you for a location where you want it installed. The default is ~/QtSDK. So
```

find ~/QtSDK -name designer

```should locate the directory that you need to add to your PATH.

---

### Post by p3aul on 2012-08-16
I'm sure you hate having to lead people by the hand like this but that simple statement lead to a whole bunch of paths, all ending in designer. here they are. Could you tell me which one I want?
```
owner@owner-desktop:~$ find ~/QtSDK -name designer
/home/owner/QtSDK/Examples/4.7/designer
/home/owner/QtSDK/QtCreator/bin/designer
/home/owner/QtSDK/QtCreator/lib/qtcreator/plugins/designer
/home/owner/QtSDK/QtCreator/share/qtcreator/designer
/home/owner/QtSDK/Desktop/Qt/4.8.0/gcc/plugins/designer
/home/owner/QtSDK/Desktop/Qt/4.8.1/gcc/bin/designer
/home/owner/QtSDK/Desktop/Qt/4.8.1/gcc/plugins/designer
/home/owner/QtSDK/Desktop/Qt/474/gcc/plugins/designer
owner@owner-desktop:~$ 


```Thanks,
Paul

---

### Post by spjackson on 2012-08-17
I haven't installed any bits of Qt for a long time, other than via Ubuntu packages, so I don't know for sure what you need to set. Also, I've never done Qt development using Netbeans, so I don't know quite how that works.

For some of the options you found, designer is a directory so you can rule those out. Perhaps I should have said
```

find ~/QtSDK -name designer -type f

```So I expect that you want either /home/owner/QtSDK/QtCreator/bin or  /home/owner/QtSDK/Desktop/Qt/4.8.1/gcc/bin . Since you are using Netbeans I assume that you won't be using QtCreator, so I think we can leave out the former.

You may also need to set LD_LIBRARY_PATH... Aren't there any instructions?

If I were you, I'd make sure I could start designer from the command line before trying it through Netbeans.

---

### Post by p3aul on 2012-08-17
I followed your logic and tried both the Creator path and the Desktop path. Neither worked. I tried running from the command line and that didn't work so I tried opening the terminal in the designer directory and typing in designer. That didn't work either. I used nautilus and navigated to the directory, double-clicked on the filename, designer. **[COLOR=Red]That worked just find.[/COLOR]**[COLOR=Red][COLOR=Black]So I know designer is installed and that it runs. Is something wrong with the path statement. Here is what it looks like now. Can you see anything wrong?

[/COLOR][/COLOR]```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/owner/QtSDKDesktop/Qt/4.8.1/gcc/:/home/owner/QtSDK/Desktop/Qt/4.8.1/gcc/bin
```I added the desktop path to the end.
Thanks,
Paul

---

