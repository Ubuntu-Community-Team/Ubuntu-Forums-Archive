---
title: "Weird, Weird Executables"
date: 2012-03-11
forum: General Help
---

### Post by wisner94 on 2012-03-11
I'm new to Linux. I've started using Ubuntu for programming @ work, and I really like the OS. But one thing is really getting at me... I can't start Netbeans. I click on the icon in the launcher: splash screen comes up, says it's loading everything, but then the splash screen closes and the Netbeans program doesn't start. I've examined the netbeans-7.1.1.desktop file, and seen that it does in fact point to the Netbeans executable in /usr/local/netbeans-7.1.1/bin.

When I try to run this executable from the command line, it looks like

```
andrew@laptop:/usr/local/netbeans-7.1.1/bin$ ./netbeans
```Like when starting Netbeans from the Launcher, the splash screen comes up, says it's loading everything, but then the splash screen closes and the Netbeans program doesn't start.

When I run the executable like this

```
andrew@laptop:/usr/local/netbeans-7.1.1/bin$ sudo ./netbeans
```I can get past the splash screen to the program.

I suspect this has something to do with file permissions, which I'm still getting a hang on. For the Netbeans executable, the listing says

```
-rwxrwxr-x  1 root root   6656 2012-03-01 19:25 netbeans
```Can anyone help me? Major thanks in advance. I've been working on this problem for several hours now, and it's driving me crazy! :confused:

---

### Post by yetiman64 on 2012-03-11
Check your system path with
```
echo $PATH
```If the executable is in a folder that is not in the system path the system won't find it when the launcher is used, but in the terminal you have already navigated to the folder and are launching from there, so it will work.

You need to add the folder /usr/local/netbeans-7.1.1/bin to the system path, to do so add the line,
```
export PATH=$PATH:/usr/local/netbeans-7.1.1/bin
```to the end of the file ~/.profile on a new line. 

~/ is your home folder and you will need to show hidden files to open .profile with gedit. If you open with gedit from the command line **do not** use sudo, it can mess with file ownerships (giving your ~/.profile to root) when used in your home folder .

Log out of your desktop and then back in, run the "echo $PATH" command again and the location should now be in the system path. If it is test the launcher again. Good luck.

Note: this is pretty generic advice above, I have no experience with netbeans and am unsure about the permissions aspect of the netbeans executable, but a glance they appear OK. 

Edit: [s]on rechecking, it **will** need sudo (or gksudo if it is a graphical app - as I said I don't know the actual program in use :-)) to operate, as it is in the root filesystem not your home directory and so is owned by root.[/s]

Strike those comments as the executable bit for others (you when launching in terminal without sudo) is set as executable but not the write "bit". 

The application must need the user to have write permissions to work so when run as root it has this but you come under the permissions of others (the last "r-x") so will fail as no write access is available to it then. 

This seems more likely the case. I realized this as some executables in root owned locations can be launched without sudo (vlc in /usr/local/bin in my install is one such example - it doesn't need the user to have write permissions for it to run) but that location is in my system path so it can be found.

Sorry for the misinformation struck out above.

Please wait for others more experienced with permissions and netbeans in particular to check this thread. yetiman64

---

### Post by yetiman64 on 2012-03-14
Sorry for the double post OP (consider this a free thread bump :)) but it just occured to me, rather than adding to the system path (if that is the problem), you could try putting the full path to the executable in the applications launcher in the "Exec=" line, this would save you from altering any other of your profiles files.

Copy the executable's .desktop (desktop configuration file) from /usr/share/applications to ~/.local/share/applications and then open it from there in gedit and alter the Exec= line putting in the full path. If it is the only executable you need to access in the bin file for netbeans it may be quicker and safer to do. Also noted if you add yourself to the group root it would probably work as the group "root" has the same permissions as the user "root" (the files owner) - that would account for the permissions aspect you noted. Cheers.

---

