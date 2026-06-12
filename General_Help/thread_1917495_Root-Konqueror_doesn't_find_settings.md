---
title: "Root-Konqueror doesn't find settings"
date: 2012-01-30
forum: General Help
---

### Post by dc_wmj2 on 2012-01-30
I'm using Kubuntu Trinity 10.10 and there is a very annoying bug: When starting something as root, the pathes get lost. E.G. root-konsole doesn't find kde-apps. So I set up the kde-paths in /etc/environment, /root/.profile /root.bashrc and can start apps from a root-konsole now. ;-P

Problem now: Root-Konqueror (and maybe other root-apps as well) still doesn't find all pathes. Started with sudo, kdesu or from a root-terminal, konqueror has a blank settings-page and doesn't remember detailed list-view.

So I looked around on the web and found out that konqueror has to be started this way to work correctly as root:

```
sudo PATH=/opt/kde3/bin:/opt/kde3/games:/opt/kde3/bin:$PATH KDEDIRS=/usr/:/opt/kde3/ KDEHOME=$HOME/.kde3 XDG_DATA_DIRS=/opt/kde3/share/:/usr/share/ MANPATH=/opt/kde3/share/man konqueror &
```This command indeed is working! 
However, when I type the same command from a root-terminal it doesn't. Anybody knows why?

I already played around with env_reset in sudoers. The first lines look like this now:

```
Defaults        env_reset
Defaults        !secure_path
Defaults        env_keep="KDEHOME,PATH"
```Starting a root-konsole from a normal konsole with sudo
```
>sudo konsole
```,
shows that the new konsole indeed is getting the KDEHOME-variable from the user.
```
echo $KDEHOME
```  outputs > /home/user/.kde3 even though it's typed into a root-terminal. However, the line 
```
echo $PATH
```leads to this output:
> /usr/bin:/bin but it should read: > /opt/kde3/bin:/opt/kde3/games:/opt/kde3/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


**Edit:**

After playing around with colors for the command-line, I noticed that a konsole started from another konsole always seem to read the bashrc-file from the parent-console - no matter which user it is called for. E.g. an xterm-window called from a root-console always shows colors from root's bashrc. It doesn't matter if it shows a root-bash or a user-bash.

---

### Post by dc_wmj2 on 2012-01-30
No answers? Somebody? My question is: How can I make this line global but overridable by the user?:

sudo PATH=/opt/kde3/bin:/opt/kde3/games:/opt/kde3/bin:$PATH KDEDIRS=/usr/:/opt/kde3/ KDEHOME=$HOME/.kde3 XDG_DATA_DIRS=/opt/kde3/share/:/usr/share/ MANPATH=/opt/kde3/share/man
KDEHOME needs to be different when kde gets started by the user and not root.

---

