---
title: "Google Chrome needing keyring access for stored passwords?"
date: 2011-03-23
forum: General Help
---

### Post by dBuster on 2011-03-23
When did Google Chrome start to access or store its passwords using the system keyring?  I do not like unlocking the keyring for web access and would like to go back to the way it was before.

Anyone know how to keep Chrome from using the keyring???  Just something leery about allowing chrome access to the keyring..

---

### Post by celldweller1591 on 2011-03-23
Try this [link]("http://askubuntu.com/.../how-to-make-chrome-chromium-remember-passwords-in-the-gnome-seahorse-keyring"), it might solve your problem.

---

### Post by dBuster on 2011-03-23
> **celldweller1591 said:**
> Try this [link]("http://askubuntu.com/.../how-to-make-chrome-chromium-remember-passwords-in-the-gnome-seahorse-keyring"), it might solve your problem.

That link was not valid...  Try again please

If it was dealing with not asking for keyring password that is not an issue.

The issue is why does all of a sudden Google Chrome need to have keyring access?  What was changed with the way it stores passwords in the last few releases that now has chrome wanting full keyring access...

---

### Post by relic70 on 2011-03-27
I've got the same problem with Chromium browser. Posted that sometime back, but still no response from anyone.

After opening Chromium it always asks to enter keyring password with a popup window before I can go to a website (bank, forum, gmail, etc.) requiring a login. Once I do that all is normal.

It happened to me when Chromium was updated from Version 9 to Version 10 automatically from update manager in Lucid.

---

### Post by dBuster on 2011-03-27
> **relic70 said:**
> I've got the same problem with Chromium browser. Posted that sometime back, but still no response from anyone.

After opening Chromium it always asks to enter keyring password with a popup window before I can go to a website (bank, forum, gmail, etc.) requiring a login. Once I do that all is normal.

It happened to me when Chromium was updated from Version 9 to Version 10 automatically from update manager in Lucid.

After further reading this new way of storing passwords is supposedly safer than the way they were stored before.  However, I do not have to enter the keyring for some other things so why in the world does it hang up loading a web page??  If it is safer can any one confirm this?  If so can it be set to not prompt for password if we are logged into the system?  Or at least make it quicker to prompt before erroring out loading a page.

---

### Post by Kixtosh on 2011-04-06
I've been struggling with this one too. I thought I must have changed a setting by mistake or something, but now that I've read this thread, I'm sure that it is something to do with an automatic Chromium update recently, as relic70 suggested. This Keyring message appears even on the websites where I have an account, but haven't ever set Chromium to remember the password.

I know that in the past, I have read comments that Chromium was not as secure as Firefox, because passwords were not stored in an encrypted format, which FF apparently does. I was still using Chromium, however, because of the way it gave me extra screen space by putting the tabs in place of the window title bar (and I like the look and feel of it, too), but I was only storing non-sensitive passwords: those not related to banking or anything like that. Chromium also seemed to work faster on older, technically challenged laptops.

So now we have these annoying pop-up Keyring messages. I've just installed FF4, and it works perfectly without such an annoyance, so I'm going to have to switch back to FF after using Chromium for the past year if I can't find a fix.

Any ideas anyone? Has a bug been filed? Is it even consider a bug, or an "enhancement"?! Surely if Firefox is secure without this, Chromium should be secure without this too.

On the other hand, if Chromium does really now store passwords safely, perhaps I can just enable the login password for Ubuntu, if that unlocks the Keyring for Chromium as well. I currently allow my profile to be logged on automatically when starting up. Has anyone tried this to see if it works? In that case I could use Chromium the way I really want it: storing 90% of my passwords, except the most security sensitive ones. I just don't want that annoying message every time I navigate to a website with a login and password to enter.

---

### Post by Kixtosh on 2011-04-06
Well, I just tried this:

- Went to System menu in the top panel,
- Selected Administration drop down menu,
- Changed the Login screen setting to "Show the screen for choosing who will log in",
- Changed the Users and Groups setting to Password: Asked on login".

Now Chromium will not require a Keyring password when I navigate to a website where I have a profile. It is necessary to change the Users and Groups setting to "Password: Asked on login". Simply showing the login screen and clicking on the user profile, without having to enter the password, does not work. Chromium will still require a Keyring password if that setting is not changed to require the password as well as showing the login screen.

Thanks to uRock (Ubuntu forum staff) who provided this suggestion in another thread related to Keyring issues.

Now, can anyone confirm whether or not passwords are stored safely by Chromium (in an encrypted format) with this new method of functioning?

---

### Post by Vesukka on 2011-07-24
> **Kixtosh said:**
> Well, I just tried this:

- Went to System menu in the top panel,
- Selected Administration drop down menu,
- Changed the Login screen setting to "Show the screen for choosing who will log in",
- Changed the Users and Groups setting to Password: Asked on login".

Thanks Kixtosh!

I took a look of settings, changed to "Show the screen for choosing who will log in", but reselected "Log in as..." after I changed my mind. Then I went in to Users and Groups and did nothing else than clicked OK (Password was already "Asked on login").
Guess what: I got rid of the Keyring prompt!

---

### Post by calande on 2011-11-18
Hello,

I have the same problem with Chrome asking for my keyring password. I cleared Seahorse's password last week, and today it's asking for my password again when I start my computer. How could I get rid of it?
Thanks,

---

### Post by calande on 2011-11-19
Any idea?

---

### Post by gandaran on 2011-11-19
> **calande said:**
> Hello,

I have the same problem with Chrome asking for my keyring password. I cleared Seahorse's password last week, and today it's asking for my password again when I start my computer. How could I get rid of it?
Thanks,
set a blank password for the keyring
open passwords and encrypted keys and delete all profiles, then create a new profile but set a blank password for this new keyring (name the new profile either login or default) 
then it wont bother you anymore asking for keyring passwords.

---

### Post by calande on 2011-11-20
@gandaran: Working fine now! Thank you very much :)

---

### Post by MikeCyber on 2013-02-22
how? I've no keys at all and don't want to change that.

---

### Post by wildmanne39 on 2013-02-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

