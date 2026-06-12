---
title: "Zenity Warning Diaolog has no cancel button"
date: 2009-11-28
forum: General Help
---

### Post by narnie on 2009-11-28
Hello,

I am having problems with Zenity not showing "Cancel" button when invoked.

```
zenity --warning --text "Windows found. Ok to delete it. Cancel to leave it alone."
```

This should result in a dialog box that has an OK button and a cancel button as shown on zenity's web page at:

[http://library.gnome.org/users/zenity/stable/zenity-message-options.html.en]("http://library.gnome.org/users/zenity/stable/zenity-message-options.html.en")

This is on a jaunty box, but my son's UNR box using karmic does the same thing.

Any idea why? And how to fix it?

Thanks,
Narnie

---

### Post by dcstar on 2009-11-28
> **narnie said:**
> Hello,

I am having problems with Zenity not showing "Cancel" button when invoked.

```
zenity --warning --text "Windows found. Ok to delete it. Cancel to leave it alone."
```

This should result in a dialog box that has an OK button and a cancel button as shown on zenity's web page at:

[http://library.gnome.org/users/zenity/stable/zenity-message-options.html.en]("http://library.gnome.org/users/zenity/stable/zenity-message-options.html.en")

This is on a jaunty box, but my son's UNR box using karmic does the same thing.

Any idea why? And how to fix it?

Thanks,
Narnie

Works fine on my system, turn off desktop effects and see if things change.

---

### Post by sisco311 on 2009-11-28
```
zenity --question --text "Windows found. Ok to delete it. Cancel to leave it alone(not recommended)."
```

---

### Post by kaibob on 2009-11-28
No cancel button here. I suspect this change was intentional.

> Don't show cancel button on warning dialogs (Claudio Saavedra) [#324100]

[http://www.mail-archive.com/gnome-announce-list@gnome.org/msg03181.html](http://www.mail-archive.com/gnome-announce-list@gnome.org/msg03181.html)

---

### Post by sisco311 on 2009-11-28
> **kaibob said:**
> I suspect this change was intentional.

+1

canceling a warning makes no sense.

---

### Post by narnie on 2009-11-28
> **dcstar said:**
> Works fine on my system, turn off desktop effects and see if things change.


I don't have any desktop effects enabled. Of note, the statement:

```
zenity --question --text="This is a test"
```

DOES give me a Cancel button. It is only the warning type that the cancel is not there.

It is also strange that my son's computer is a very fresh install with karmic and nothing really added to it. Pretty stock karmic.

I'm dubious that this is on 2 different computers in 2 different versions of ubuntu.

What version of ubuntu did it work for you on?

Thanks,
Narnie

---

### Post by narnie on 2009-11-28
> **sisco311 said:**
> +1

canceling a warning makes no sense.

If it is a warning like do you want to overwrite a file and you want to, you select OK. If you don't want to, you select Cancel and it doesn't overwrite the file.

You want something that will give a little more UMPH than just a question.

Plus, the project's documentation says it should place a cancel button, but it doesn't. So something is messed up.

Narnie

---

### Post by kaibob on 2009-11-28
> **narnie said:**
> Plus, the project's documentation says it should place a cancel button, but it doesn't. So something is messed up.

The project documentation was last revised in August 2004. According to the developer, the cancel button was removed from zenity warning dialogs in version 2.17.1, which was released in December 2006.

---

### Post by sisco311 on 2009-11-28
never mind

---

### Post by dcstar on 2009-11-29
> **narnie said:**
> I don't have any desktop effects enabled. Of note, the statement:

```
zenity --question --text="This is a test"
```

DOES give me a Cancel button. It is only the warning type that the cancel is not there.

It is also strange that my son's computer is a very fresh install with karmic and nothing really added to it. Pretty stock karmic.

I'm dubious that this is on 2 different computers in 2 different versions of ubuntu.

What version of ubuntu did it work for you on?


Sorry, I didn't understand your problem as a **Warning** cannot/should not be cancelled and therefore does not offer this option - it is just a message.

As others (and you) have discovered, a **Question** has both options and that is exactly as it is documented in the man page.

---

