---
title: "Setting up the default Panel layout"
date: 2012-06-06
forum: General Help
---

### Post by Azdour on 2012-06-06
Hi,

In Xubuntu 12.04 we have users that come and go and their accounts are removed. What I have been trying to do is tailor the xfce4 panel and I have the first part solved.

I have set up xfce4 in a template account how I want it to look for new users. I then copy the xfce4-panel.xml to /etc/xdg/xfconf/xfce-perchannel.xml. 

When I create new users they get this default panel, but I have two issues I'm currently trying to resolve:

1. Launchers

In the template account I have added launchers to the top panel. Having looked at xfce4 these launchers are defined in ~/.config/xfce/panel. If I copy this panel directory to /etc/xdf/xfconf and create a new user account the launcher appears on the panel but has no icon and clicking on it does nothing.

What I can see is that the /etc/xdg/xfconf/panel is not copied/created in the users account. The global xfce4-panel.xml contains the launchers plugin details, but this is not being created in the new user account.

2. Places Launcher

I've added the Places launcher to the template panel. This launcher appears in the new user account but when you click on it the list does not contain everything, e.g. its missing folders like Documents, Download etc...

The strange thing is that if I launch Thunar and then go back to the Places launcher they have appeared. Thunar must be populating something when it starts for the first time ever. What I really want is it to be populated from the start.

Any help would be greatly appreciated.

---

### Post by LewisTM on 2012-06-06
1) The directory is wrong. It should be /etc/xdg/xfce4/panel

2) You would have to execute xdg-user-dirs-update, which generates file ~/.config/user-dirs.dirs
The template is /etc/xdg/user-dirs.defaults but it needs to be filled-in by the above command. Normally this command is run early at login.

---

### Post by Azdour on 2012-06-06
Hi,

Thanks.

The typo was in actually in my typing this thread :)

I've checked and the panel directory I copied from the template account is in /etc/xdg/xfce4 and it never gets copied when I create a new user account and log in as that new user. I've done quite a bit of google searching and while there are docs out there for xfce4 there seems to be nothing concrete about creating a global panel for new users.

Thanks also for xdg-user-dirs-update, I can probably script it for when the user logs in.

---

### Post by LewisTM on 2012-06-06
I've never experimented myself but what about /etc/xdg/xdg-xubuntu/xfce4/panel ?
The entire /etc/xdg/xdg-xubuntu tree seems more complete with lots of default config files and dirs.
/etc/xdg/xdg-xfce is a symlink that point to the above so it must be the one.

---

### Post by Azdour on 2012-06-06
Hi,

I'm trying to use xdg-user-dirs-update. I create a new account, login, go to terminal and run the command:

```

xdg-user-dirs-update --set DOWNLOAD ~/Downloads

```

But the Places launcher does not list the Download folder.

---

### Post by LewisTM on 2012-06-06
This should work as much as your .config/user-dirs.dirs file will be modified. Log out and back in to see the effect.

The Places plugin does not show user dirs, only GTK bookmarks. User dirs appear in Thunar's Go menu. They are not much use except to give certain folders a special icon e.g. the Pictures folder will have a camera or a photo icon. Some applications can use them to quickly identify where to look for files.

FYI GTK bookmarks are in ~/.gtk-bookmarks

EDIT: I realize that I have misled you in thinking that user-dirs would populate your Places menu. I don't know how GTK bookmarks are created for new users. Sorry :(

---

### Post by Azdour on 2012-06-07
Hi,

Ok, for anyone who would like to know this is how I was able to share my xfce panel set-up.

1. Create a template account (lets call this user template) and set up the panels and launchers as you want them.
2. In the /etc/skel directory create a directory called .config:
```
sudo mkdir /etc/skel/.config
```
3. Into this directory copy the .config/xfce from the template account:
```
sudo cp -r /home/template/.config/xfce /etc/skel/.config
```

Now when you log in as a new user they should see the panels and launchers that you set up as default.

The question about the Places and the missing folders. From what I understand when Thunar is run for the very first time it creates a .gtk-bookmarks file in the format:
```
file:///home/<username>/Documents Documents
```

To fix this so that a new user can immediately see the folders under Places I do the following:

1. In /etc/X11/Xsession.d create a file called 95x11bookmarks:
```

cd /etc/X11/Xsession.d
gksu leafpad 95x11bookmarks

```
2. In this file add:
```

if [ -f ~/.gtk-bookmarks ]; then
    echo "" > /dev/null
else
    echo "file:///$HOME/Documents Documents" > ~/gtk-bookmarks
    echo "file:///$HOME/Downloads Downloads" >> ~/gtk-bookmarks
    echo "file:///$HOME/Music Music" >> ~/gtk-bookmarks
    echo "file:///$HOME/Pictures Pictures" >> ~/gtk-bookmarks
    echo "file:///$HOME/Videos Videos" >> ~/gtk-bookmarks
fi

```
My understanding is that the files in Xsession.d are run when a user logs in. If the user is new there will be no .gtk-bookmarks, so the above script creates the file.

---

