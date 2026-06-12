---
title: "What causes ssh to popup a login dialog?"
date: 2010-11-25
forum: General Help
---

### Post by azzid on 2010-11-25
I wrote a script the other day, to make it easier to connect to a windows machine I can only reach through a ssh tunnel.

This is what i cooked up:
```
#!/bin/bash

# Set some variables
HOST=<ssh server>
TUNNELUSER=<ssh user>
TUNNELPORT=3389
TUNNELHOST=<remote rdp server>
RDPUSER=<rdp username>
RDPLANG=sv

# Establish tunnel
/usr/bin/ssh $HOST -l $TUNNELUSER -L $TUNNELPORT:$TUNNELHOST:$TUNNELPORT -N &

# Save tunnel PID
TUNNELPID=$!

# Wait until tunnel is up
while ! $(echo "" | /bin/nc localhost $TUNNELPORT)
do
	: #echo nothing
done

# Do stuff with tunnel (connect RDP server)
/usr/bin/rdesktop -a 16 -x l -f -T'Terminal Server Client' -u$RDPUSER -k $RDPLANG localhost

# Shut down tunnel
kill $TUNNELPID

```

It works (imho) REALLY good! :D

As a final step I created a launcher for the script and now have a button to push whenever I want to connect.

When I push said button gnome will conjure a dialog allowing me to supply my ssh password, after that I can login to the windows machine as expected.

Now the question: How/Why is gnome conjuring that dialog?

I tried doing something similar under debian the other day, and there I get no pw-dialog and hence I cannot make the connection.

I could just set up unauthenticated ssh-login, but it triggered my curiosity, does anyone know how this stuff works?

Please, if you can, explain it to me! :)

---

### Post by efflandt on 2010-11-25
If you do **ps aux | less**, you will find something like this:

efflandt  1584  0.0  0.0  11988   304 ?        Ss   Nov23   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session

That allows you to give your password (or pass phrase for a key) once and not have to enter it again for the same credentials during that gnome session.

See **man ssh-agent**

Back in the old days, when I was running Slackware or SuSE, I would make an alias for startx that would run ssh-agent before doing startx.

---

### Post by matt_symes on 2010-11-25
Hi

Use keys for authentication. They are transparent and safer.

or use ssh-agent.

Kind regards.

---

### Post by azzid on 2010-11-26
Thank you for you answers guys!

My question however was not how to make authentication automated or more secure, my question was what makes ssh popup a dialog under gnome.

I made some more investigations myself, and it turns out there is a program called ssh-askpass that is responsible for the dialog.

I have yet to try to install/configure it under debian to see if I can make debian behave as nicely as Ubuntu, but now atleast I know what is making the magic happen on my machine.

---

### Post by azzid on 2010-11-27
It was ssh-askpass-gnome that was the difference.

To get the feature running under debian all I had to do was: ```
apt-get install ssh-askpass-gnome
```

---

### Post by matt_symes on 2010-11-27
Hi

> **azzid said:**
> It was ssh-askpass-gnome that was the difference.

To get the feature running under debian all I had to do was: ```
apt-get install ssh-askpass-gnome
```

I'm glad you got your problem sorted. :) I think sometimes we (help on the forums) try to look for problems that are not there. At least we are trying to help :)

Kind regards

---

### Post by azzid on 2010-11-27
I sincerely appreciate all the input, without your replies I would not have figured it out.
That the path to solve the issue is less than straight is just natural. ;)

Thank you!

---

