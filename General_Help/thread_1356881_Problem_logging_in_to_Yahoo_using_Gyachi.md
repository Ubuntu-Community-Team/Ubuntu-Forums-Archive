---
title: "Problem logging in to Yahoo using Gyachi"
date: 2009-12-16
forum: General Help
---

### Post by xeddog on 2009-12-16
For a few months now I have been having a problem logging into Yahoo using Gyachi.  Here is what happens:
```

GyachE Improved 1.2.2 
http://gyachi.sourceforge.net/
 Plugin Loaded:  'GyachI-spellcheck-plugin-gtkspell' 
 Plugin Loaded:  'GyachI-sound-plugin-ALSA' 
 Plugin Loaded:  'GyachI-libNotify' 
 Plugin Loaded:  'MCrypt' 
 Plugin Loaded:  'Blowfish-Internal' 
 Plugin Loaded:  'Gpgme' 
 Loaded 6 plugins from '/usr/lib/gyachi/plugins'.

[12/16/2009 12:31:03]    CONNECTED: type /help for help

Current Buddy List: (comma separated buddy list)   (friends online in RED)

Current Buddy List:  (comma separated buddy list)  (friends online in RED)


  ** WARNING: TOO MANY DIALOG MESSAGES HAVE BEEN OPENED TOO QUICKLY (Possible Flood or Boot Attack from a malicious Yahoo user?) -  Dialog Messages will be temporarily disabled for 2.5 minutes to help protect your system, and default actions will be taken for all 'confirmation' dialogs.
** Info Message: Could not connect to server:
f5.yahoofs.com **
** Info Message: Could not connect to server:
f5.yahoofs.com **
[12/16/2009 12:31:13]    Disconnected from Yahoo!    See Ya!  Online for  0 : 00 : 10

[12/16/2009 12:31:15]      ** You have been disconnected from Yahoo! [ Error receiving from socket: 9 ] **
[12/16/2009 12:31:15]    Disconnected from Yahoo!    See Ya!  Online for  350276 : 31 : 15

** Info Message: You have been disconnected from Yahoo!
Error receiving from socket: 9 **
```

At the same time as this, I get 7 small little dialog boxes with ```
Could not connect to server:
f5.yahoofs.com 
```in them with a "OK" button. (Note - same message as in the first text messages shown above)

Once this happens I am screwed.  My only option is to quit Gyachi and not even try to start it again.  I have tried a couple of times and it hangs the entire system, not just Gyachi.  I have to ctl-alt-F1 to get a console, do a ps -A to find the Gyachi process number and then kill it.

I have tried a couple of things to resolve this and nothing works.  I have tried using YMSG-15 and YMSG-16 protocols, and I have tried many of the servers listed in the pulldown list.  The ONLY Yahoo server that lets me in is "cn.scs.msg.yahoo.com".  For some reason it seems to work just fine, but since it is the only server that works, I am wondering for how long.

I have had this problem with at least versions 1.2.1 and 1.2.2 of Gyachi, run on 32-bit Ubuntu Intrepid and Jaunty on two different machines, and 64-bit Karmic. 

If anyone knows anything else to try I'm all ears (eyes??).  Or if there is any other debugging info that I can get just let me know.  I know there are other IM clients out there, but Gyachi has the feature set that I want and none of the others do.  Specifically, the photo sharing capability, and the ability to select multiple buddies and type one message that is sent to all of them instead of having to retype or copy/paste.

One more note.  I have been trying to go back to the "normal" Yahoo server (scs.msg.yahoo.com) about every two weeks or so just to see if it automagically starts working again.  A few days ago it did just that.  It worked using scs.msg.yahoo.com for four days and then went belly up again.  This was on a 32-bit Jaunty and 64-bit Karmic.

Thanks,

xeddog

---

### Post by justborn on 2009-12-20
did u try logging in with only your username,without "@yahoo.com"?

for GYachE Improved HOWTO,refer:
[COLOR="Red"][http://ubuntuforums.org/showthread.php?p=8531391#post8531391]("http://ubuntuforums.org/showthread.php?p=8531391#post8531391")
[/COLOR]

---

### Post by xeddog on 2009-12-21
> did u try logging in with only your username,without "@yahoo.com"?

Yes.  I have never used the "@yahoo.com" part.

xeddog

---

### Post by xeddog on 2010-01-03
I had something interesting happen today loggin into Yahoo.  I tried switching the server back to scs.msg.yahoo.com and I was able to get logged in just fine.  About 30 minutes or so later I noticed a bubble in the upper right corner of my screen that my daughter logged into Yahoo, and at the same time MY session went berserk.  And by that I mean that I got all of the messages I usually get as described in my original message. 

THEN, just after that my daughter came down and was telling us (my wife and I) that there is someone else on the Internet that has her exact same email address on Yahoo.  Not similar, but EXACT same.  My daughter gets some of this other persons emails.  So if the Yahoo email address is the same then the YIM id is probably the same too.  I wonder if that is what is causing my problem with Gyachi?!?!?

xeddog

---

### Post by loell on 2010-01-03
I noticed that your problem has been going on for quite a while now and that you've been constantly looking for solution.

 I suppose I haven't asked you this but have you tried using another account? and does the symptom still persist?

---

### Post by needhelppeeps on 2010-01-12
it isnt just him. I am getting the exact same thing from time to time.

---

### Post by xeddog on 2010-01-13
Hi Loell,  

I think I have figured out what might be triggering my problem and it is my daughters Yahoo id.

I just tried logging in with my wife's yahoo id and it worked.  I did notice one peculiarity.  In the chat window after the "CONNECTED" message, there were two lines of "***ignoring" which seemed to be ok.  Then there were THREE sets of lines showing "Current Buddy List:".  In all three sets of lines, the list of users was identical.  But the third line was slightly different.  The last line had one userid that was highlighted, and then "(friends online in RED)" was appended to the line.  This probably doesn't matter a whole lot since it works, but there it is.

Anyway, while I was logged in with her account I noticed that my daughter was not logged in.  I went to my daughters computer and logged her into her YIM account.  Came back downstairs to my computer and my Gyachi had gone berserk.  Back upstairs and shutdown her YIM, and I was able to log back in with my wife's id again.  

I did the same procedure all over again using my own id this time.  As long as my daughter is NOT logged in I am fine.  As soon as she comes online, my Gyachi takes a crap.

Hope this helps.


xeddog

---

### Post by loell on 2010-01-13
Interesting find, what's your network setup in your home? is it shared connections with a router?

---

### Post by xeddog on 2010-01-18
Loell - 

Sorry it has taken so long to respond, but yes, all computers are networked within my house.  I have a DSL Elite (6MB  d/l speed) coming into my house.  It, of course comes into my DSL modem which is attached to my Netgear router.  The router is then connected to a 48-port HP Procurve switch.  All of the other computers, printers, and what have you are all connected to this switch EXCEPT for my daughters stuff.  She has her own router that all of her stuff is connected to, and her router is then connected to my switch.  Everything is all on the same subnet, and all of the comptuers, including her equipment, all use my router as the default route.  

You may be asking why I put a router in her room instead of just using mine.  Well, at the time she had a Wii in her room and it had to be connected wirelessly.  The wireless router I had at the time was a real POS and the signal in her room was very weak, even though the straight line distance is only about 30 feet or maybe 40 tops.  So I set her router up to act as a wireless access point more than anything else.

Anyway, that's my story and I'm stickin' to it.  I might just add though, that this YIM problem is the only thing we have found that doesn't work right.  That might (and probably does) have something to do with some other person having the same Yahoo email address as hers.  Since the email address is the same, the YIM id would be too.  She still hasn't looked into it yet so I think it's about time to (figuratively) kick her butt and have her get on it.

xeddog

---

### Post by RonaldCruz on 2010-03-13
Hi guys,

I found something about the error "f5.yahoofs.com". I eliminated the error by disabling or unchecked the settings below: Menu -> Tools -> Edit my display image...
1. Show display in IM windows
2. Show avatars on my buddy list
3. Show my avatar on friends' buddy lists

I observed this when I checked this 3 items I get these errors. I'm not so sure why but it seems that it is fetching something from that server maybe pictures or avatars but wasn't able to get any that's why it gives that kind of error.

Note: unchecking this items will disable your avatar or your display image. You and your friends will not able to see your display image or avatar as well as theirs.

Hi Loell,

Please help to verify this. Thank you so much!:D

---

### Post by loell on 2010-03-13
what version are you using?

---

### Post by d3v1150m471c on 2010-03-13
Your daughter's account is probably getting locked. Have her login with her ID into yahoo mail and it will clear this problem up if this is the case.

---

### Post by RonaldCruz on 2010-03-15
> **loell said:**
> what version are you using?

Hi Loell,

I'm using 1.2.6.
From PPA of Darwin.

---

### Post by zeroseven0183 on 2010-03-17
Same problem here but with version 1.2.2. I can connect to Pidgin and webmessenger.yahoo.com but not in GyachE.

Tried adding @yahoo.com in username but to no avail

---

### Post by xeddog on 2010-03-22
d3v1150m471c - Nope.  She is free to use her account whenever and where ever she chooses.  It's just that when she logs in, gyachi goes banahners.

RonaldCruz - this seems to be working for me too.  For now.  :D

This is with Version 1.2.5 running on 64-bit Karmic.

xeddog

---

### Post by xeddog on 2010-03-26
Just thought I'd update this by saying it has been three days now since I tried the circumvention by RonaldCruz, and my Gyachi is still working.  I have seen my daughter log in and out several times and have even IM'd her and it is all good now.  Except for the avatar thing, but I don't really care about that anyway.

xeddog

---

