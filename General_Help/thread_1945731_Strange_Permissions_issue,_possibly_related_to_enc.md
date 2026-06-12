---
title: "Strange Permissions issue, possibly related to encrypted home dir:"
date: 2012-03-23
forum: General Help
---

### Post by skralljt on 2012-03-23
Some issues in my ubuntu installation have cropped up, all revolving around permissions.  However, I can't seem to find an error in auth.log, dmesg, or syslog that conclusively points to what the problem is.  I have searched here, arch linux forums, and google in general to no avail.  I have installed two alternative desktop environments (openbox and lxde) to see if it was just an issue with xfce but they exhibit the same problems:
1.  In thunar or pcmanfm if I click on another drive or partition not mounted by fstab, I get a message saying permission denied instead of the file manager mounting the partition for me.
2.  In the graphical logout dialog, I can only select logout.  Reboot and Shutdown are greyed out.  Possibly related: in lightdm, the little control box in the top right of the screen sometimes lets me select shutdown or reboot but usually if I click on it, no menu drops down.  
3.  Perhaps most importantly, when I run "users-admin" either from the commandline or from the program menu it does not let me write any changes to users and groups.  I can click on buttons but for all of them except groups no dialog box comes up.  Running it from the command line does not yield any errors.  If I go into the groups dialog for a user and add somebody to a few groups and then exit out of users-admin and restart it, the changes I have made are reset and the user is removed from those groups. The only error I get is "GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed"
4.  I made another account with an encrypted home directory and then tried to login from lightdm with her account but got a lightdm login loop; that is, after successfully giving credentials lightdm goes to a black screen showing some of the boot process and then returns to the lightdm screen, waiting for me to select a user and login.  Removing the requirement for a password for this user didn't let me bypass this.
Perhaps the only useful clue I have is from the .xsession-errors logfile which always has this entry: "(polkit-gnome-authentication-agent-1:11017): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files"
In my research of my host of issues, polkit is frequently identified as the culprit but in none of these threads is there ever any resolution.  People just reinstall or go back to windows.  Help me!

---

### Post by skralljt on 2012-03-23
I should also add that I have permission for sudo, though starting users-admin with gksu doesn't allow me to change anything.

---

### Post by skralljt on 2012-03-29
NOBODY CAAAARRRRES!!!  
Strangely, today I can mount other drives using pcmanfm and I can access "users and groups" and make changes.  For now, the problem is averted, but not yet solved.

---

