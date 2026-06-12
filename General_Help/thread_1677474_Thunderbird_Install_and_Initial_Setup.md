---
title: "Thunderbird Install and Initial Setup"
date: 2011-01-28
forum: General Help
---

### Post by ddjolley on 2011-01-28
I have installed Thunderbird (apt-get install thunderbird).  As is typical, when I first launch Thunderbird after having completed the installation I am presented with the "Mail Account Setup" dialog box which should request basic setup information.  My problem is that this dialog box is completely empty.  There is nothing.  I tried removing the ~/.thunderbird directory and re-launching Thunderbird; but, the same problem again presented itself.  Has anyone else see this strange behavior; and, more importantly does anyone know what to do about it?  BTW I am running Ubuntu 10.04.1.  Thanks for any input.

          ... doug

---

### Post by Habitual on 2011-01-28
> **ddjolley said:**
> My problem is that this dialog box is completely empty. 

Doug: 
Installing is one thing, Account Setup is something else entirely.
You have to fill those values in.
and every time you delete ~/.thunderbird, you are in effect, starting all over. so try to avoid that action.

---

### Post by ddjolley on 2011-01-28
> You have to fill those values in.

I totally understand that.  The problem is there is no place for me to fill anything in.  The "Mail Account Setup" dialog box is completely empty.  By that I mean that there are no text boxes in which data can be entered and there are no prompts.  It's just completely empty.  

> and every time you delete ~/.thunderbird, you are in effect, starting all over

That's precisely why I deleted ~/.thunderbird.  I wanted to start over to see if I would get a dialog box that was populated with what it is supposed to have.  I did not.  I just got the same old empty dialog box.

Thanks for the input.

          ... doug

---

### Post by Habitual on 2011-01-28
Doug:

Have you de-installed/purged Thunderbird and re-installed?
does thunderbird in a terminal yield any "error" or diagnostic warnings?

Alternatively, you could create another user on the system and login as that user and run Thunderbird, just to see if the issue is specific to you or the system.

version?
```
thunderbird -v
```

---

### Post by ddjolley on 2011-01-28
> Have you de-installed/purged Thunderbird and re-installed?

I've done one better.  I completely re-installed Ubuntu and then re-installed Thunderbird.  Same result.

> does thunderbird in a terminal yield any "error" or diagnostic warnings?

Nope.  It's quiet.

Thanks.   I was hoping that I was making some simple procedural error.   It's beginning to sound like this is a problem that is not commonly seen.  That's not good. :)

Thanks for the input.

         ... doug

---

### Post by Habitual on 2011-01-28
Doug:

```
thunderbird -v
```
?

I am subscribed to this thread, but I am going to bed and will return in about 9 hours, give or take...

John

---

### Post by ddjolley on 2011-01-29
[FONT=monospace]> thunderbird -v

Thunderbird 3.1.7

    ... doug
[/FONT]

---

### Post by Habitual on 2011-01-29
Doug:

Have you tried "...create another user on the system and login as that user and run Thunderbird, just to see if the issue is specific to you or the system."?

---

### Post by ddjolley on 2011-01-29
> Have you tried "...create another user on the system and login as that user and
> run Thunderbird, just to see if the issue is specific to you or the system."?

I created a second user and launched Thunderbird with the same identical results.  So, the condition is NOT peculiar to that particular user.  Thanks.

         ... doug

---

### Post by Habitual on 2011-01-29
Doug:

This suggests turning off Desktop Effects:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/615779](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/615779)


System->Preferences->Appearance->Visual Effects from "Normal" to "None".

Let me know...

---

### Post by ddjolley on 2011-01-29
> System->Preferences->Appearance->Visual Effects from "Normal" to "None".

Viola!!!  THAT FIXED THE PROBLEM!  

[> https://bugs.launchpad.net/ubuntu/+s...rd/+bug/615779]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/615779")

Interesting and (if you're going to be installing Thunderbird) must-know info.

Thanks so much for the help.

        ... doug

---

### Post by Habitual on 2011-01-29
You're Welcome.

Glad it worked out.

---

### Post by ddjolley on 2011-02-01
I'm sorry, I'd still like to further clarify some aspects of this issue.

> System->Preferences->Appearance->Visual Effects from "Normal" to "None".

Should I switch back to "Normal" after I have setup my account?

[> https://bugs.launchpad.net/ubuntu/+s...rd/+bug/615779]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/615779")

So, this is a bug.  Will it likely be an issue that is addressed in an upcoming update?  How would I know if a fix has been included in an update?   Assuming that I have applied a bug fix in the form of an update, how do I test to see if it is working properly.

Thanks for any input.

         ... doug

---

### Post by Habitual on 2011-02-01
Yes, you can switch back (turn on Desktop Effects) after setting up the account.

But my opinion is that some other dialog boxes in Thunderbird (or elsewhere) may also be affected.

I'd follow [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/615779](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/615779) for details about a "fix"...

It seems unclear.

---

### Post by SeijiSensei on 2011-02-01
Just an aside, but this isn't a problem in Kubuntu.

---

### Post by topher-t-mill on 2011-02-01
install Evolution!

---

