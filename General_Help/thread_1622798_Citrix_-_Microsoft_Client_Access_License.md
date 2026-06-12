---
title: "Citrix - Microsoft Client Access License"
date: 2010-11-15
forum: General Help
---

### Post by browneyedemily on 2010-11-15
Hello-

I apologize if this is a re-post. I'm very new...

I use Ubuntu. I've been using Citrix and my TS license needs to be reset and I can't figure it out. To reset I've had to use a Windows reg file. The wonderful (rolling my eyes) IT guy said it won't work in Ubuntu, but it's been done before, I just can't figure it out now.

Anyone have any suggestions? :)

Em

---

### Post by browneyedemily on 2010-11-15
I apologize again - my husband fixed it and gave the below info re: solution, in case anyone else has the same problem:

# Remove /etc/icalicense directory
$ sudo rm -Rf /etc/icalicense

#Note where your ICAROOT is
$ echo $ICAROOT

#Remove ICAClient directory
# Make sure that ICAROOT is really what you want to kill, otherwise this could do bad things
$ sudo rm -Rf $ICAROOT

# Remove local configuration directory
# rm -Rf ~/.ICAClient

# Reinstall the client

---

