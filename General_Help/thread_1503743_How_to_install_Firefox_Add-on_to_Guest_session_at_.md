---
title: "How to install Firefox Add-on to Guest session at login?"
date: 2010-06-07
forum: General Help
---

### Post by Naggobot on 2010-06-07
Adding Firefox add-ons to Guest Session?

I wanted to include Add-on to Ubuntu Guest Session  Firefox.
Is there a proper or better way to do this? Procedure I used was as follows

1. Login to Ubuntu to a user account with sudo privileges (later sudoer account). 
1. Switch to Guest Session
2. Install relevant Add-ons
3. Check what the home folder of the Guest Session is. It should be something like /tmp/guest-home.xxxxxx where xxxxxx = six random characters. 
4. Switch to sudoer account
5. Open terminal and type

```
gksudo nautilus
```6. With Nautilus browse to /tmp/guest-home.xxxxxx
7. Select from Nautilus topmenu to show hidden files
8. Copy folder .mozilla
9. Browse to /user/share/
10. Make new folder GuestFox
11. Browse to folder GuestFox
12. Paste .mozilla folder to GuestFox folder
13. Browse with Nautilus to /user/share/gdm/guest-session/
14. Double click guest-session-setup.sh and select Display to edit script with gedit. 
15. Find line with following command

```
cp -rT /etc/skel/ "$HOME"
```16. Before previous line add command
[#CODE]cp -rT /usr/share/GuestFox/ "$HOME"[#CODE]
17. Save file
18. Close gedit
19. Close Nautilus
20. Switch to Guest Session
21. Log out from guest session
22. Log in to sudoer account
23. Switch to Guest session
24. Open home folder Places -> Home folder
25. Select view->show hidden files 
26. Verify that .mozilla folder exists
27. Start Firefox to see if the add-on works. 

I tested this with Flashblock and it seemed to work. I also admit that since I did the thing for the first time it was not that straight forward for me, but above procedure should work. Please verify / comment if it works or if you have some problems. 

If there is an easier or more proper way to accomplish this or if there is some risk associated with this please comment. With quick Googling I was unable to find straight forward method. There is a way to install Add-ons to all users from command line using -install-global-extension but this was not what I wanted to do. I wanted the Add-on just for the temporary guest account.

---

### Post by Naggobot on 2010-06-08
bump?

---

### Post by ducanhhoang on 2010-07-03
thank for the nice guide, I try Adblock Plus and it works.

---

### Post by Naggobot on 2010-07-06
I noticed that after upgrading the Firefox the guest session kept checking the compatibility of add-ons. (Meaning that every time new guest started the Firefox it checked once). To overcome this I just recopied the .mozilla folder. There might be better way to update the profile but did not want to spend time figuring it out from scratch. 

My apologies for not updating this thread at the time. 

Nice to hear that this was of help to someone.

---

### Post by ducanhhoang on 2010-07-06
I also try to copy every hidden files in the home folder of guest session to the GuestFox folder and all my settings for guest session seem to be kept like Firefox add-ons
Hope this can help for someone :D

---

### Post by Naggobot on 2012-02-01
Time flies. 

It is 2012 and Firefox updated so I had to update the Guest profile. 

I am so happy that I wrote this at the time since I would have been in lot of trouble while trying to remember how the thing was set up.

---

### Post by oasit on 2012-02-28
Put the addon in /usr/lib/firefox-addons/extensions/

You have to remane the addon to its id. You see the id when you unpack the xpi-file and open the install.rdf file. The id is between the <em:id> tags. The addon is now automatically installed for all users. The drawback of this solution is that the user cannot update the addon itself.

Best solution is maybe to install from the repo if available (search for xul-ext-...)

---

