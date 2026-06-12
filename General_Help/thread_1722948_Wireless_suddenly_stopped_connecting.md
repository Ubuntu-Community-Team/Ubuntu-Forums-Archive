---
title: "Wireless suddenly stopped connecting"
date: 2011-04-06
forum: General Help
---

### Post by Wuxin on 2011-04-06
I have Ubuntu 10.10 on IBM ThinkPad T43.  When I go to authenticate my connection, my password doesn't seem to be recognized.  More specifically, in the authentication box, there are two switches "connect" and "cancel."  Only the "cancel" switch is highlighted.  Above the box where I normally insert my password is another box which has within it:
WEP 40/128-bit Key (Hex or ASCII)
I don't recall that message as having been there before.  Any help will be greatly appreciated!  I can't get online with my laptop!  I've never had this problem before!

---

### Post by grahammechanical on 2011-04-06
You are either putting in the wrong password, such as your log in password and not the wireless key of passphrase, or you are using the wrong encryption method. What encryption method is the modem/router set for? If it is set for WPA and network manager is trying to connect with WEP encryption (as it seems to be) then even the correct password will fail.

Right click the icon snd select Edit connections. Select the wireless tab and select your connection then click Edit. Select Wireless security and make sure that the mode is set to WPA and WPA2 Personal. You can tick the box Show password to see if the password has not been changed somehow.

Why not at the same time set the connection to connect automatically? Network manager remembers passwords, even wrong ones. A wrong password can cause problems like this as network manager tries it best to get a connection.

Regards.

---

### Post by Wuxin on 2011-04-06
[SIZE=3][FONT=Times New Roman]Yes, I have a separate key password--one that I have used since installing Ubuntu--and I've tried it, repeatedly.  Believe me, it's not working.  I've no idea what encryption method the router is set for; I've always used the same word and it's worked for me.

What icon are you suggesting I "right click" on?  And where exactly do you find the setting of "WPA" or "WPA2"?  How would the computer have switched to WEP encryption if it hadn't been set up that way originally?  Hey, if this works, I really don't care!  (But I am curious...)

How do you set it to connect automatically?  That would be a good way to do things--unless your computer is stolen, in which case I wouldn't want to make things easier on the thief!

Thanks for your helpfulness!
[/FONT][/SIZE]

---

### Post by Wuxin on 2011-04-06
[FONT=Times New Roman][SIZE=3]Okay, I followed your advice and here's what happened.  When I got to the wireless connection box I selected the wireless tab and selected my connection
and clicked "Edit."  I then selected "wireless security" and made certain the connection was WEP in my case, not WPA.  I clicked the password box and lo and behold, a portion of my password (not all of it) was missing!  I added the additional digits but the "apply" button at the bottem of the box wasn't highlighted--only the "cancel" button was.  So I can't extend the password to its rightful full phrase.  

I don't know how this happened but it's crazy me!  Do I need to insert the
WEP key somewhere?  Thanks again for your help.
[/SIZE][/FONT]

---

### Post by grahammechanical on 2011-04-06
What you could do is delete the connection and create a new one. Right click the network manager icon, select Edit connections, Select the wireless tab, select your connection and click delete. Close the boxes.

You can also get to it by System>Preferences>Network connections. The dialog box that appears when you edit the connection has a check box at the top that you can tick to connect automatically.

If someone stole your computer they would presumably take it outside the range of your wireless modem and so need to set up their own connection. Do you have a log in password? Then you are not making it easy for a thief.

Now, left click the network manager icon and select your wireless connection from those available and enter the pass phrase when asked to authenticate. Make sure the encryption is set to WEP.

WPA is a more secure method of encryption than WEP. It is a later development. I made assumptions in trying to guess what was wrong. The encryption method of the computer has to match the method set in the modem/router. When we experiment trying to learn how to do things with the operating system we may change things and not notice that we have mixed things up. As you now know we can alter the encryption method. I was guessing that something like that may have happened. It is worth checking these things. I mess things up myself when I experiment to learn how to do things. Such as putting in my log in password instead of the wireless key. This is why I mentioned it.

Regards.

---

### Post by Wuxin on 2011-04-06
[FONT=Times New Roman][SIZE=3]You were right on target!  It was indeed the mistake of putting my password in the wireless key.  What I needed was the default identification on my modum--*that* was what finally got me up and running.  Now, is it possible to *change* the default key of the modum to something more easily remembered?  I notice when I run the system update manager the "key" is requested before the system will begin downloading.  Usually it's my password that will start that process.  There are quite a few occasions when you need that WEP key and it's a pain to have look at the bottom of the router every time.

Yes, when you experiment around all kinds of things can happen.  But the amazing thing about Linux--and it's why I like it!--is that the problem is usually my not knowing what to do.  Very seldom is it the OS.  In Windows, you can be doing absolutely nothing wrong and you have problems.  Thank you for your helpful advice!
[/SIZE][/FONT]

---

