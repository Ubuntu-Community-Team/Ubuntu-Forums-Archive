---
title: "cannot delete user"
date: 2010-08-01
forum: General Help
---

### Post by Oblivion4234 on 2010-08-01
Hello I am having a problem with my login labeled "mysql" with the command 

# groupadd mysql
# useradd -g mysql mysql

this is of course all within the confines of being super user. What I am having trouble with is that I cannot delete the user through the terminal using the command userdel but to no avail, it states that the user mysql is still logged in even though I have restarted the computer and logged in only to my root account. Whenever I try to log into mysql account it gives me multiple error messages something about the ICE authority and nautilus and when i get past these and onto the home screen, there is  nothing, the wallpaper is there but there are no icons and no tool-bars, I cannot shutdown or get to a terminal while on the dysfunctional user. I cannot delete the user because it states I am logged in even though I am not. Any help would be much appreciated, thank you.
P.S. I checked my File System and in the folder Home it has my folders for my two normal logins but it does NOT have a folder for the mysql login.

---

### Post by fyo on 2010-08-01
> Whenever I try to log into mysql account it gives me multiple error messages something about the ICE authority and nautilus and when i get past these and onto the home screen, there is nothing, the wallpaper is there but there are no icons and no tool-bars, I cannot shutdown or get to a terminal while on the dysfunctional user.

I had this part happen to me when I deleted a user (not logged in) through the "Users and Groups" administration applet. Trying again, this time selecting "keep files" (home dir was already gone), solved the problem.

That doesn't help you, of course, if your mysql user is logged in... (The ICEAuthority errors, though, are almost certainly because the home dir no longer exists).

If you are using your mysql user as the name implies, you might want to try shutting down your mysql process.

---

### Post by Oblivion4234 on 2010-08-01
Thank you for your input fyo, could you please explain to me how to end the process, as you can tell i am just a beginner to mysql and linux in general so some help would be great.

---

### Post by Oblivion4234 on 2010-08-01
thank you fyo, i stopped the mysql process and sure enough I was able to delete the user, thank you for your help

---

