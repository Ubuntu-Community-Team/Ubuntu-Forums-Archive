---
title: "locales ... again"
date: 2011-09-29
forum: General Help
---

### Post by MakOwner on 2011-09-29
I see a bunch of posts about this, and several pointers to fixes.. none of which work.

Is there a fix??

I have the annoying-as-hell: 
```

bash: warning: setlocale: LC_CTYPE: cannot change locale (en_US)

```
every time i press tab in a terminal.
Oddly enough *sometimes* it goes away, but the errors of a missing directory are always present with the locale command:

```

 locale            
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US
LC_CTYPE="en_US"
LC_NUMERIC="en_US"
LC_TIME="en_US"
LC_COLLATE="en_US"
LC_MONETARY="en_US"
LC_MESSAGES="en_US"
LC_PAPER="en_US"
LC_NAME="en_US"
LC_ADDRESS="en_US
LC_TELEPHONE="en_US"
LC_MEASUREMENT="en_US"
LC_IDENTIFICATION="en_US"
LC_ALL=

```


What freaking directory is missing???

/var/lib/locales/supported.d/
 contains "en" and "local"

locale-gen completes with no error:
```

w:~$ locale-gen 
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.

```


Why is it so hard to get an error message that communicates some information?  Argg... 


Can anyone give me clue?

---

### Post by matt_symes on 2011-09-29
Hi

What is the output of

```
cat /etc/default/locale
```

Kind regards

---

### Post by MakOwner on 2011-09-29
> **matt_symes said:**
> Hi

What is the output of

```
cat /etc/default/locale
```

Kind regards

```

 cat /etc/default/locale 
LANG="en_US.UTF-8"

```

---

### Post by matt_symes on 2011-09-29
Hi

....and the output of

```
locale -a
```?

Kind regards

---

### Post by MakOwner on 2011-09-29
> **matt_symes said:**
> Hi

....and the output of

```
locale -a
```?

Kind regards

```

w:~$ locale -a
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX
en_AG
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8

```

Bound to be something I'm missing...

---

### Post by matt_symes on 2011-09-30
Hi

Sorry for the delay. Timezones and work. Lets try a quick test.

Open a terminal and type

```
export LC_ALL="en_US.utf8"
```

Then type

```
locale
```

Do you still get the error ? (This is only a temporary test)

If that does not work try

```
export LC_ALL="en_US.UTF-8"
```

and perform the same test. What happens ?

Kind regards

---

### Post by MakOwner on 2011-09-30
> **matt_symes said:**
> Hi

Sorry for the delay. Timezones and work. Lets try a quick test.

Open a terminal and type

```
export LC_ALL="en_US.utf8"
```

Then type

```
locale
```

Do you still get the error ? (This is only a temporary test)

If that does not work try

```
export LC_ALL="en_US.UTF-8"
```

and perform the same test. What happens ?

Kind regards

Yes, that clears the error and gives a clean locale output.
exporting LC_CTYPE does too.
But only for that terminal session.

Somewhere the variables are not being set in the creation of the session -- BTW when I sudo to root, the environment changes and the errors go away, so it is most likely just this login ID -- however there are no other login ids on this laptop.

And sorry for the length of time to reply, sleep and work and all :)

---

### Post by matt_symes on 2011-09-30
Hi

Well your issue is a miss-match in your locales. 

Your default is set to en_US.utf8, but your locales are being set to en_US. You do not seem to have en_US on your system as shown by the locale -a command.

So you have 2 options.

1. Set your locales to the default locale of en_US.utf8
2. Generate the locales for en_US on your system.

What would you like to do ? 

Please understand, i am no expert at setting the locales but i think this is what you need to do.

BTW: I have to do some running about so i may not be able to respond until tomorrow. It will depend on how busy i am.

Kind regards

---

### Post by MakOwner on 2011-09-30
> **matt_symes said:**
> Hi

Well your issue is a miss-match in your locales. 

Your default is set to en_US.utf8, but your locales are being set to en_US. You do not seem to have en_US on your system as shown by the locale -a command.

So you have 2 options.

1. Set your locales to the default locale of en_US.utf8
2. Generate the locales for en_US on your system.

What would you like to do ? 

Please understand, i am no expert at setting the locales but i think this is what you need to do.

BTW: I have to do some running about so i may not be able to respond until tomorrow. It will depend on how busy i am.

Kind regards


Wonder where en_US went, and why of the system default is UTF-8 how did it get changed? an update?

In the meantime, how do I set locale for the login?

No problem on time, I have a ton of things too.  
Thanks for the help!

---

### Post by matt_symes on 2011-09-30
Hi

Let's generate the locales for en_US. Open a terminal and type..

```
sudo locale-gen en_US
```Enter password as normal and then type

```
locale -a
```Post results back here.

> Wonder where en_US went, and why of the system default is UTF-8 how did it get changed?

It may be the other way around.

Kind regards

---

### Post by MakOwner on 2011-09-30
clean, but I need to reboot just to check.
```

:~$ locale -a 
C
en_AG
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

```

---

### Post by matt_symes on 2011-09-30
Hi

Blimy!! That was a quick return post after my last post :)

Kind regards

---

### Post by MakOwner on 2011-09-30
> **matt_symes said:**
> Hi

Blimy!! That was a quick return post after my last post :)

Kind regards

Instant email notification for the thread -- and I'm working where I have web and email access :)

---

### Post by matt_symes on 2011-09-30
Hi

Did that fix the issue ? If so then please mark this thread as solved.

Kind regards

---

### Post by MakOwner on 2011-09-30
That did it.  No longer seeing the error when using tabe completion!
That fixes the sumptom, wonder why it happened?

Thank you for the help!!!!!

Marked thread as solved.  
In case some one is searching on thie, the error message was:
```

bash: warning: setlocale: LC_CTYPE: cannot change locale (en_US)

```

The fix was to generate the missing language/locale file:

```

sudo locale-gen en_US

```

---

