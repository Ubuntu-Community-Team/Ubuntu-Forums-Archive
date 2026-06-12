---
title: "Login screen changed."
date: 2012-05-12
forum: General Help
---

### Post by poudigne on 2012-05-12
My login screen has suddenly change and I have a little preference for the Default one.
Here's my login screen
{see attach #1}
Here's how (I think) it's supposed to look like
{see attach #2}
I know it's useless but I like my thing beautiful =)

Hoo and btw, if anyone has tips to change splash screen, scroll bar and ubuntu sound for Mac OSX. I'd like some link to a tutorial :)

 Thank.

---

### Post by Bucky Ball on 2012-05-12
Have you updated lately? Please attach pics rather than putting them in the body of the post. Hit the 'Go Advanced' button under the post edit window and use the paper clip icon to attach. ;)

---

### Post by poudigne on 2012-05-12
Thanks for the tips, I dont post really much. 

About the update, I make my apt-get upgrade pretty much everyday. All I can say is that I try 2 other different Desktop Environment Gnome and Cairo-Dock (this is how it's called :-? )

---

### Post by Bucky Ball on 2012-05-12
Well, that looks like you have the Gnome login screen presently. I have never seen the other one because I have never installed 11.10. But I have the gnome one and run 10.04 LTS (and have it on a 10.10 install also).

Not a fix but perhaps a clue for further investigation ...

---

### Post by deadflowr on 2012-05-12
The first screenshot is the old gdm(gnome display manager) login screen. The second is the new Lightdm(light display manager) login screen. It comes default in 11.10 and up. Here's a link to hopefully fix it for ya:

[http://askubuntu.com/questions/58528/whats-the-difference-between-gdm-and-lightdm]("http://askubuntu.com/questions/58528/whats-the-difference-between-gdm-and-lightdm")

---

### Post by poudigne on 2012-05-12
> **deadflowr said:**
> The first screenshot is the old gdm(gnome display manager) login screen. The second is the new Lightdm(light display manager) login screen. It comes default in 11.10 and up. Here's a link to hopefully fix it for ya:

[http://askubuntu.com/questions/58528/whats-the-difference-between-gdm-and-lightdm]("http://askubuntu.com/questions/58528/whats-the-difference-between-gdm-and-lightdm")

Thank for your help I just wasn't searching with the right terms. Thank you.

---

### Post by deadflowr on 2012-05-12
Just for kicks I tried out the command in the link I posted myself ,as I have both installed, I usually use lightdm but I switched it over to gdm. I found killing X didn't switch it, but a full reboot did. Now time to reswitch again as I like seeing my wallpaper on the login screen.(That's a function of it on 12.04. It matches your user wallpaper background with user name, so switching user at the login will change the background to that users wallpaper:usually warty-something.png.)If it works for you mark this thread solved.

---

### Post by poudigne on 2012-05-13
It worked, but i have to enter my profile's name to log in, I don't have the users list.

---

