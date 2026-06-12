---
title: "Please help!!"
date: 2010-12-19
forum: General Help
---

### Post by David2011 on 2010-12-19
Hi i have just picked up an Eee pc 701sd small laptop,i used it a couple of weeks ago and it was fine,i have just took it out the drawer to wrap it up for my daughters xmas,i turned it on to stick a screen saver on,but when it boots up there is no icons on screen,just a blue backround & a small toolbar at the bottom which has several icons on but they dont seem to be able to get me on to the home screen?? can anyone help me sort this i would be most gratefull for any help.

Kind Regards
David.

---

### Post by sikander3786 on 2010-12-19
Welcome to the forums :-)

Are you sure Ubuntu is installed there? If yes, which version?

---

### Post by David2011 on 2010-12-19
Hi i am not sure whats installed,i am used to xp but i think its linux that comes with this laptop?

---

### Post by nothingspecial on 2010-12-19
Don`t panic :D

Is it linpus?

Find terminal in your menus and put these in
```

cat /etc/issue
```

and

```
cat /proc/version
```

Post what the terminal says back here.

---

### Post by David2011 on 2010-12-19
i'm sure its linux thats installed its the 2008 model?

---

### Post by nothingspecial on 2010-12-19
I edited my post above, do you have access to a terminal?

If so, post the output of those 2 commands.

Do you have a username and password?

---

### Post by tredegar on 2010-12-19
I have an eee701-4G. It came with xandros linux, which I replaced with ubuntu (10.04 now).

The desktop you describe doesn't sound like the default factory-install at all.

Is this a second-hand EEE? In which case, it could have *anything* installed. 

What happens if you mouse up to the very top of the screen? Is there a menu "auto-hiding" there?

---

### Post by David2011 on 2010-12-19
I dont have access to a terminal,the person i got the laptop from purchased it new so nothing has been changed or updated i assumed its linux after i checked on google which operating system this model number runs on? is there any way to find out as obv i cant click on any icons?

---

### Post by nothingspecial on 2010-12-19
Right now you have a couple of options.

There are plenty of people here who can help you get a fully functioning ubuntu netbook in less than an hour.

Or you can ask on the xandros forums.

Or you can hope someone who is familiar with xandros sees this post.

That`s 3 not a couple :p

If you want to go Ubuntu download from here

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I`m not saying do it, it`s just that since you're here ...............

---

### Post by sikander3786 on 2010-12-19
Can you post a screen shot some how?

Or do you have access to an Ubuntu or anyother Linux Live CD or even ISO image? You can burn that to CD or a USB disc and boot from that and perform some commands while in the Live CD environment.

---

### Post by tredegar on 2010-12-19
Did you get the manual and the CD with the EEE?

IIRC there's an option at boot to restore it to its factory-state by pressing something at boot-time (F9 ? I cannot now remember, and I'll need to go on a hunt for the original manual). This will _only_ work if it has the original xandros OS.

> the person i got the laptop from purchased it new
Sorry, but it can't be both "the 2008 model" and "new"!

There is a lot of information on the EEEs over at
[http://wiki.eeeuser.com](http://wiki.eeeuser.com) and [http://forums.eeeuser.com](http://forums.eeeuser.com)

---

### Post by David2011 on 2010-12-19
the laptop doesnt have a disk drive i am using my own vaio at the moment i will try and upload some images

---

### Post by David2011 on 2010-12-19
sorry the laptop doesnt have a disk drive? i am using my own vaio at the moment on here
will try and get some photos on

---

### Post by David2011 on 2010-12-19
Photo

---

### Post by tredegar on 2010-12-19
It's an EEE701 -Confirmed.
I know it does not have a CD drive, but it did come with a cd-rom with some utilities.
Your picture does NOT show the standard xandros desktop - there should not be a bar at the bottom of the screen (IIRC).
If you mouse up to the top of the desktop, is there an auto-hiding menu there?

For the second time, do you have the user manual?

---

### Post by David2011 on 2010-12-19
I only have the laptop and charger sorry,when i scroll up there are no hidden menu's.i am 100% sure its linux thats installed there are some small icons at the bottom including a yelow happy face,red no entry sign,power saver,time etc but it will only let me in the power saver thats all..?

---

### Post by sikander3786 on 2010-12-19
**tredegar** seems experienced with that stuff and is helping you, I know.

I have another opinion though that has already been mentioned earlier. If you want to, and if you've got all the resources, you can put Ubuntu Netbook or Ubuntu Desktop on that machine. The only things you currently need is a working DSL Internet Connection and a USB Drive and another working computer with either Windows or Linux to create the Ubuntu startup USB. And we can guide you till the end with that ;-)

Hope **tredegar** can help you fix that.

---

### Post by David2011 on 2010-12-19
many thanks for all your help i have pressed F9 and restored it to factory settings which seems to have done the trick guys,many thanks for your time and replys.

---

### Post by tredegar on 2010-12-19
OK
I found my EEE manual (I am surprised, I am not usually that organised).

Another thing to try: Disconnect power cable & battery (turn over, slide lock(s), pull).
Press ON button for 30 sec.
Reconnect battery & power cable.
Turn on.

If that fails...
There's a reasonable chance that it still has the original xandros.
To restore it to as-new from the factory follow these steps, it's worth a try, as it seems to be well broken at the moment:

Make sure charger & battery are plugged in.
Press F9 during bootup (just keep pressing it madly)
You get a menu.
Highlight **Restore Factory Settings**
Press Return

If this works, at the next start, you'll have to select language etc. Just make sensible choices.

If it helps, I have found the User Manual on the CD (I didn't really _keep_ it, more like never got round to throwing it out!), and I'll happily email it to you if you PM me your address. It's 5.5MB

Do not post your email here, it'll be harvested by bots.

To avoid disappointment, Santa might have to go shopping before the week is out, but we'll try our best.

Good luck.

Edit:
I type Waaay too slowly.
Glad you fixed it.
Don't forget to check out the eeeuser links I gave earlier
/Edit

---

### Post by nothingspecial on 2010-12-19
> **David2011 said:**
> many thanks for all your help i have pressed F9 and restored it to factory settings which seems to have done the trick guys,many thanks for your time and replys.

Great news :D

---

