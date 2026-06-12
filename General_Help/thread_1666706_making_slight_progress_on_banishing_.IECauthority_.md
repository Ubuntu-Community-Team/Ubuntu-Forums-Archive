---
title: "making slight progress on banishing .IECauthority demon, little help though?"
date: 2011-01-14
forum: General Help
---

### Post by hUNJ on 2011-01-14
Hey good people,

So, "unable to update .IECauthority hit me yesterday in a big way. After trying all sorts of suggested remedies in the [solved] and unsolved threads, it became quite evident that the chown and chmod would not work coz ubuntu cant find the "file or directory specified" by .IECauthority. {pardon the n00bspeak}

So i looked around for the "new user" option, i.e. creating a new user so i can log in. That worked. i got to terminal and used sudo adduser guest and now i can at least log in but, predictably i cant access the files of my home directory that was under my "owner" login. 

Any suggestions on how i can access these files as my new "guest" user alias?

I feel like im so close to beating this friggin .IECauthority error though i am well aware i brought all this misery upon myself coz i just had to have the extra skins for this particular screenlet...okay now im rambling. Any help would be appreciated.

hUNJ

---

### Post by hawthornso23 on 2011-01-14
Look for .ICEauthority

That is ICE not IEC

I suspect a simple spelling mistake is the cause of most of your problems with fixing this issue.

---

### Post by johnaaronrose on 2011-01-28
I am now getting 'Problem with configuration server  /usr/lib/libgconf2-4/gconf-sanity-check exit with status 256'. I've  tried logging in with Session of 'Failsafe Gnome' -  sometimes it's OK  & sometimes it isn't.
 
 PS I first used sudo chown user:user /home/user/.* to correct the.ICEauthority problem following advice in thread 
[http://ubuntuforums.org/showthread.php?p=10405265#post10405265](http://ubuntuforums.org/showthread.php?p=10405265#post10405265)
Perhaps I should have used sudo chown /user:user /home/user/.ICEauthority rather than sudo chown user:user /home/user/.*
I've subsequently tried sudo chmod 1777 /tmp, which made no difference

---

### Post by johnaaronrose on 2011-01-30
Login is now working fine. I found a message (I've forgotten where) about 'deleting' .ICEauthority. The suggested method is:
mv /home/user/.ICEauthority /home/user/.ICEauthority.bak 
(where user is your login id).

This has the advantage that the .ICEauthority file can be restored by
mv /home/user/.ICEauthority.bak /home/user/.ICEauthority 
 even if the above method doesn't work.

Since both my login users only gave a 'blank' desktop (i.e. no menus or  quick launch icons) when I attempted the standard login, I logged into  the user with administrative privileges by changing the Session (at the  bottom of the screen) to root login (i.e. not one of the Gnome ones)  after selecting/keying in the login id but before keying in the  password.

After login I discovered that a much smaller .ICEauthority file had been  created (1kb versus 60+) for that user. I opened a Terminal &  repeated the command for my other user but with sudo before mv. I then  restarted and was able to login for my first Administrative user, logout  & login successfully for my second Desktop user.

---

