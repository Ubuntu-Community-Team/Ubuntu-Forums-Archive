---
title: "running Firefox/skype in a sandbox (dummy user)?"
date: 2010-01-30
forum: General Help
---

### Post by alexito84 on 2010-01-30
Maybe you are also concerned about the safety and privacy of your data.
I am and therefore I would likt to create some kinf of a sandbox, but I am unsure 
how to accomplish this and would be very happy about your ideas and sughgestions.

My plan (upto now - open for other approaches) has been to
create another user account with limited access (indeed as limited as possible as preveliged as necessary).

I would like to run potentially risky program under a different user account.
examples for "risky progams" would be
*web browsers (risk of privacy and virus - with sometimes inevitable Javascript)
*distrusted programs as skype (proprietary commercial)

With this secondary user account (I call it "bogus account") I would like to accomplish
that the program in worst case can only access the files inside this bogus account home dir(which is not too problematic as it would remain empty *hehehe*)

I though on simply:
1. creating a new user account in System->Administration->Users and Groups
2. using the command : gksu -u bogususer firefox 
   to start the program at best within my own session (not having to switch between sessions).

I searched the web for this kind of sandbox safety measure but unsuccessfully
After all I still think that the PLUS in linux would be the well defined user right and hence the possibility of my "sandbox"

any help and comments very welcome

---

### Post by alexito84 on 2010-01-30
[UPDATE]

I have added the bogus user account "unpriv" in System->Administraion->User and Groups. I the "Add User"-Dialog I have choosen the Profile option "Unprivileged" (expecting this to be the most restricted user).

I have been able to run the command: su unpriv
on the shell and received an error trying to run the program gedit 

```
(gedit:3261): Gtk-WARNING **: cannot open display: :0.0
```this means it is not possible to directly run any x-server program inside the session of my normal user account while using the identiy (and restrictions) of the bogus user account.

using the command 
```
xhost + localhost
```prior to the "switching to the bogus account" enabled me to run programs like firefox or gedit.

Is there a way to fine tune, what the bogus account is having access to?
I would really very much like to restrict it as much as possible.

---

### Post by alexito84 on 2010-01-30
[Update 2]

Now that I can run certain aplication (most important a copy of skype and firefox) inside 
my session (using the id of the bogus user account)  I have some mor diffuculties.

It is obvisously possible to start X (graphical applications) but sometimes as with
totem or nautilus I receive another erro message (when trying to run them from the bogus account) see below


```
(totem:3505): Unique-DBus-WARNING **: Unable to open a connection to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

it seems to be a problem of the DBus. 
I have no real idea yet how to tackle this problem. 

any help on how to make skype run in an restricted way is therefore still very appreciated

alex

---

### Post by IgnorantGuru on 2010-02-05
I recently wrote a program that does this...
[http://igurublog.wordpress.com/downloads/script-sandfox/](http://igurublog.wordpress.com/downloads/script-sandfox/)

Very easy to use...  you just install it and run it.  It's been working very well.

There are also more complex solutions for this but after looking at the alternatives I went with this approach.

---

