---
title: "STDIN argument to passwd"
date: 2009-09-03
forum: General Help
---

### Post by dizwell on 2009-09-03
I've written a bash script to create a new user. It prompts for that user's new password. I'm using Zenity to put a graphical gloss on things. So my code looks like this:

```
export PASSWD=$(zenity --entry --title="New Password Required" --entry-text="fredsmith" --text="`printf "The new User account needs a password.\nPlease specify one now."`" )

echo $PASSWD | passwd $USER --stdin

```

That code works fine in Redhat, Suse and some others. But in Ubuntu, I'm getting an error that "passwd: unrecognized option '--stdin'", which means that the user-specified password for the new user isn't being echoed and therefore, not being set.

The various options for passwd are being displayed at this point, of course, but none of them seem to offer a way out of this impasse.

How do I get a user to type in a password that will then be passed through to the passwd application so that it gets set properly?

All help gratefully received!

---

### Post by dizwell on 2009-09-04
<bump>

---

