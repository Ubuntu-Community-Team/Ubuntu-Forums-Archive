---
title: "I can not login. It takes me back to the login screen."
date: 2012-06-01
forum: General Help
---

### Post by cogitator on 2012-06-01
Hello. Thank you for your time to read this topic. Problem explanation: when I am trying to login, and after a successful one, immediately after that it shows a black screen (with a bunch of text) and then it takes me back to the login screen again.
I do not have any idea why this happens. I tried to login by pressing CTRL+ALT+F1. I read in the forums that a member with a partially similar problem delete the ".Xauthority". But, none of these particular ways fix the login process.
I logged in as a 'guest' just to use the browser and look for advice. If you have any idea about how this may be fixed, please let me hear. Thanks in advance!

---

### Post by mchamartin on 2012-06-01
Sounds exactly like what just happened to me a couple minutes ago.  All I did was click on the drop down menu to specify that I wanted to use Gnome (which it should have been set on already) and then I logged right in.  This is the only time I've ever experienced this though so I don't know if it's just coincidental that it worked after I did that or if that actually somehow solved whatever the problem was.  Give it a shot and see I guess.

---

### Post by cogitator on 2012-06-01
Hi, **mchamartin**. Thank you for your reply. I selected 'Gnome' and then tried to login, but the same thing happened again. Also, I tried to login selecting each time a different item from the drop down menu, but again it was an unsuccessful try.
[A maybe relevant hind: yesterday I was dealing with github (for the first time) in my machine (with stuff like cloning repositories etc). I just mention it as a potentially cause for that problem . . .]

---

### Post by Shadius on 2012-06-01
> **cogitator said:**
> Hello. Thank you for your time to read this topic. Problem explanation: when I am trying to login, and after a successful one, immediately after that it shows a black screen (with a bunch of text) and then it takes me back to the login screen again.
I do not have any idea why this happens. I tried to login by pressing CTRL+ALT+F1. I read in the forums that a member with a partially similar problem, delete the ".Xauthority". But, none of these particular ways fix the login process.
I logged in as a 'guest' just to use the browser and look for advice. If you have any idea about how this may be fixed, please let me hear. Thanks in advance!

I've experienced that problem too. Although, I fixed it with a reinstall, I believe you can try recovery mode. See if that works. Otherwise, you'll have to be patient for another user to offer a definite solution.

---

### Post by steeldriver on 2012-06-01
it does sound exactly like the .Xauthority problem

there is another file ~/.ICEauthority that will do the same thing if it becomes unwritable to the user - I suggest you try again at the TTY and do 

```
sudo rm ~/.Xauthority ~/.ICEauthority

```at least it's quick to try and may save you having to take more drastic measures

if you're interested you can 

```
ls -al ~/.*authority

```first just to see what the permissions/ownerships are

---

### Post by cogitator on 2012-06-01
Hi, **steeldriver**. This is the whole process of my try:
1. CTRL+ALT+F1  --> and I login
2. ls -al ~/.*authority  --> and there is the .Xauthority file but not the .ICEauthority
3. sudo rm -v ~/.Xauthority ~/.ICEauthority  -->  it says that .Xauthority is deleted and that it did not find a file named .ICEauthority
4. ls -al  -->  the .Xauthority file disappears
5. CTRL+ALT+F7  -->  back to the login panel and, I enter the password to login, but the black screen appears again and finally it takes me back to then login panel

I tried this process many times with the same results (yes, in step 2 the .Xauthority appears again).

---

### Post by steeldriver on 2012-06-01
ah well it was worth a try - at least you have eliminated that possibility

you could have a look at your ~/.xsession-errors to see if there is anything helpful

also I don't think you said what version/desktop but if it uses lightdm there are session greeter logs at

/var/log/lightdm/x-0-greeter.log
/var/log/lightdm/x-1-greeter.log

etc. (and probably something similar for gdm in /var/log/gdm/)

that's about as far as I can get you - after that there are ways to reset/reinstall the desktop but those will depend which version/desktop you are using I think

---

### Post by flemur13013 on 2012-06-01
Since you can login as guest, if all else fails try adding a new user - "adduser".  See if that login works; then you can copy over (non-login! - like ~/.mozilla w/addons, etc) stuff from your old account, and optionally delete the old account, and rename the new one to the old one. (see: $ ls /usr/sbin/user*)
(Edit: copy your old ~/. account somewhere before deleting it, then maybe just copy the things you need as your need them; the only things I'd probably copy would be .wine and .mozilla.)

---

### Post by rasmus91 on 2012-06-01
I had something that seemed like the same problem, except i couldn't log in at all, not even as guest user.

Anyways, I ended up reinstalling the system, seemed like the easy way out :P

---

### Post by Shadius on 2012-06-01
In my search to find an answer to help you, I've come across many answers which talk about the method you already did. That method worked for *some*, but not all. I also came across a bug report. The method that you tried is what I keep finding as the solution. As one of the user's suggested, you could try to add another user account and just copy your original account's files or reinstall.

---

