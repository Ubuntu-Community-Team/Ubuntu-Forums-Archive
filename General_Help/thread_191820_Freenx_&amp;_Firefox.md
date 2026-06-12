---
title: "Freenx &amp; Firefox"
date: 2006-06-08
forum: General Help
---

### Post by SKP-student on 2006-06-08
Hello people.

We have here, at my workplace, a small project involving a xubuntu server and several clients connecting to it via freenx.
We have no exact control of the people logging in, as they are located in another room in this building.
We've created users with the name pc1 - pc9.
The problem is, when two people log into one account, for instance pc5. The first user will open firefox on his machine. When the second user tries to open firefox on his machine following error message will pop up:
> Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

What I'd like to know, is if there is a way around this problem, so that multiple users can use firefox simultaneusly while still using the same account, i.e. pc5.

Secondly, I'd like to know if there's a way to stop users from shutting down the server from the client. The only option they may have access to, is logout.

Thanks for your time

---

### Post by graigsmith on 2006-06-08
Why don't you give every user their own account name. That way they have their own name and password. It would be more secure, and you wouldn't have to worry about processes interfering with one another.

---

### Post by SKP-student on 2006-06-08
As I mentioned in the previous post, we have no control of who logs in.
The accounts are to be used in an Open Learning Center, available for all students on the school.
That's around 800 people.

As it is now, we just want to give people a chance to use ubuntu, if they want so.

If it IS not possible, I guess we may have to dedicate an account to each computer then.

---

### Post by norman_ on 2006-06-10
Does that help?
[http://kb.mozillazine.org/Firefox_:_FAQs_:_Run_more_than_one_instance_in_Linux](http://kb.mozillazine.org/Firefox_:_FAQs_:_Run_more_than_one_instance_in_Linux)
[http://jeroencoumans.nl/journal/multiple-firefox-versions](http://jeroencoumans.nl/journal/multiple-firefox-versions)

---

### Post by mejy on 2006-06-10
Not sure if this is what you want, but I can run epiphany on multiple X servers and I can't with firefox - you could see if epiphany will work in your current enviroment.  And its a better browser, anyway, so its not like ur missing out on anything :mrgreen:

---

### Post by mannheim on 2006-06-10
[QUOTE=mejy]Not sure if this is what you want, but I can run epiphany on multiple X servers and I can't with firefox - you could see if epiphany will work in your current enviroment.  And its a better browser, anyway, so its not like ur missing out on anything [/QUOTE]

Unfortunately, my experience with epiphany is that it is the one app that I can't make work under freenx (see attached screenshot -- that's what I get on trying to launch epiphany). Perhaps this is related to an error message I get at startup, saying something about the dbus session not running? I don't know if this problem is just me.

---

### Post by mejy on 2006-06-10
[QUOTE=mannheim]Unfortunately, my experience with epiphany is that it is the one app that I can't make work under freenx (see attached screenshot -- that's what I get on trying to launch epiphany). Perhaps this is related to an error message I get at startup, saying something about the dbus session not running? I don't know if this problem is just me.[/QUOTE]
Try 'dbus-launch epiphany'

---

### Post by tsb on 2006-06-10
I don't have any experience with Freenx, but wouldn't allowing only one user per login name solve the issue?

---

### Post by mannheim on 2006-06-10
[QUOTE=mejy]Try 'dbus-launch epiphany'[/QUOTE]

Wow! That worked -- thanks.

---

