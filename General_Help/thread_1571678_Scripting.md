---
title: "Scripting"
date: 2010-09-09
forum: General Help
---

### Post by Jonny87 on 2010-09-09
I've been starting to have a play with scripting, I'm still learning the basics though.
I have one little question that I was hoping someone could help me do.

I want to have the script display a nice little graphical thing to indicate that the script has finished running. preferably some sort of customizable message with an OK button to close it. Even better if it looks proper as though it was always an Ubuntu app.

can anyone help me with this?

---

### Post by Mr Nemo on 2010-09-10
Try zenity. It's a program used to create dialog boxes and other alerts/messages.
Here are two pages that came up with a quick google search.

[http://linuxmanpages.com/man1/zenity.1.php](http://linuxmanpages.com/man1/zenity.1.php)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

I've only used zenity a little, but if you want a simple message that appears when a script finishes try something like this:

```

zenity --info --title="Name of script" --text='Script completed!'

```

That will display a nice info box with your message. Just put it at the end of your script.
You can do a lot of cool things with zenity, just check the man pages and google for examples.
Note: You must use single quotes (' ') if you want characters such as '!' to show up.

---

### Post by Jonny87 on 2010-09-10
> **Mr Nemo said:**
> Try zenity. It's a program used to create dialog boxes and other alerts/messages.
Here are two pages that came up with a quick google search.

[http://linuxmanpages.com/man1/zenity.1.php](http://linuxmanpages.com/man1/zenity.1.php)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

I've only used zenity a little, but if you want a simple message that appears when a script finishes try something like this:

```

zenity --info --title="Name of script" --text='Script completed!'

```That will display a nice info box with your message. Just put it at the end of your script.
You can do a lot of cool things with zenity, just check the man pages and google for examples.
Note: You must use single quotes (' ') if you want characters such as '!' to show up.

Thanks, thats exactly what I'm looking for.

---

