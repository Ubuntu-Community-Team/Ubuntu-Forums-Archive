---
title: "Changing &quot;Root&quot; User login name?"
date: 2006-03-02
forum: General Help
---

### Post by DOtSlaSHuCantCME on 2006-03-02
Is it possible to change my "Root"User login name to something else, without having to start from scratch :( 
                                        TY.

---

### Post by newuser111 on 2006-03-02
No.

Why would you want to change the root account name?  Do you realize how many important system processes run at 'root'?

---

### Post by DOtSlaSHuCantCME on 2006-03-02
[QUOTE=newuser111]No.

Why would you want to change the root account name?  Do you realize how many important system processes run at 'root'?[/QUOTE]


Well! never thought i would  be keeping Ubuntu,  i was just "trying it" so i picked a silly name for root,and im definetly keeping Ubuntu ,its just that eveytime i fire up my terminal and see the name Wolfbutt#  :mrgreen: i want to change it ...oh well!

---

### Post by newuser111 on 2006-03-02
[QUOTE=DOtSlaSHuCantCME]Well! never thought i would  be keeping Ubuntu,  i was just "trying it" so i picked a silly name for root,and im definetly keeping Ubuntu ,its just that eveytime i fire up my terminal and see the name Wolfbutt#  :mrgreen: i want to change it ...oh well![/QUOTE]

i think you mean changing your machine name, not 'root' im pretty sure it can be done

---

### Post by mlind on 2006-03-02
root user is entirely different user, a guy who has access to all ares. In ubuntu
it's disabled by default.

You can create new user and copy folders & files that contain user-specific settings,
like desktop layout or music player playlists. These settings can be copied between
users but It's not the easiest task to do if you don't know what you're doing, but it's
possible. You can identify "user-specific settings" cuz those have  with .  as prefix, 
like .gnome2/ or .asoundrc.

You can test what happens by creating new user,
then doing

```

export NEW_HOME=/home/newuser
cd $HOME
tar cpf - . | tar xvf - -C $NEW_HOME

```

where NEW_HOME gets the value of newly created users home dir.
tar command will copy files to new users home dir and preserve their permissions.
I guess you could same with cp -R.

---

