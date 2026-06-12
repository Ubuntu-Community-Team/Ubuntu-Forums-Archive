---
title: "Evolution terminal command"
date: 2009-07-10
forum: General Help
---

### Post by kindofblue89 on 2009-07-10
In Evolution, is there a way to compose a new mail message by just running a terminal command? 
I was hoping to link the command to a function key as a shortcut.

---

### Post by michy99 on 2009-07-10
```
evolution mailto:test@test.com
```This will open a compose message window addressed to [email]test@test.com[/email]. Then you can change the address to whatever you want.

---

### Post by kindofblue89 on 2009-07-10
Thanks! Man, Linux make things so easy!

---

### Post by VCoolio on 2009-07-10
To make it complete, you can do this:

```
evolution mailto:address@domain.com?subject="type your subject between quotation marks"\&body="type your message between quotation marks"\&attach="/path/to/file/to/attach"
```


Remember to put subject and message etc. between quotation marks to enable spaces and characters that otherwise would be interpreted by the shell. If you want a line break in your message body insert %0A (the middle one is a zero, nut o as in opera) like:

evolution mailto:address@domain.com?subject="type your subject between quotation marks"\&body="type your message between quotation marks %0AThis is on a new line"\&attach="/path/to/file/to/attach"

If you want more attachments just keep adding \&attach="/path/to/file"
I haven't figured out how to insert multiple recipients. Anyone?

---

### Post by michy99 on 2009-07-10
> **VCoolio said:**
> To make it complete, you can do this:

```
evolution mailto:address@domain.com?subject="type your subject between quotation marks"\&body="type your message between quotation marks"\&attach="/path/to/file/to/attach"
```


Remember to put subject and message etc. between quotation marks to enable spaces and characters that otherwise would be interpreted by the shell. If you want a line break in your message body insert %0A (the middle one is a zero, nut o as in opera) like:

evolution mailto:address@domain.com?subject="type your subject between quotation marks"\&body="type your message between quotation marks %0AThis is on a new line"\&attach="/path/to/file/to/attach"

That's a bit of overkill for a command to attach to a hotkey, which is what he asked for.

---

### Post by VCoolio on 2009-07-10
Sorry, didn't read that right; but anyway use it for (nautilus-)scripting purposes. And the question at the end stands. His question answered, now another. That one may be useful for him too.

---

### Post by kindofblue89 on 2009-07-10
I appreciate it. Thank you.

---

### Post by acreech on 2009-07-13
> **VCoolio said:**
> To make it complete, you can do this:

```
evolution mailto:address@domain.com?subject="type your subject between quotation marks"\&body="type your message between quotation marks"\&attach="/path/to/file/to/attach"
```


Remember to put subject and message etc. between quotation marks to enable spaces and characters that otherwise would be interpreted by the shell. If you want a line break in your message body insert %0A (the middle one is a zero, nut o as in opera) like:

evolution mailto:address@domain.com?subject="type your subject between quotation marks"\&body="type your message between quotation marks %0AThis is on a new line"\&attach="/path/to/file/to/attach"

If you want more attachments just keep adding \&attach="/path/to/file"
I haven't figured out how to insert multiple recipients. Anyone?

That is really cool. Is there a way to also send it from the command line too? I would like to setup a bill pay reminder that would email me and remind me when to pay monthly bills also relatives birthdays, and other things that I commonly forgot to do on time. The hang up is being able to actually finish the message off by entering a command to send it. 

Thanks for any suggestions.

---

### Post by kindofblue89 on 2009-07-13
> **acreech said:**
> That is really cool. Is there a way to also send it from the command line too? I would like to setup a bill pay reminder that would email me and remind me when to pay monthly bills also relatives birthdays, and other things that I commonly forgot to do on time. The hang up is being able to actually finish the message off by entering a command to send it. 

Thanks for any suggestions.

I know this does not answer your question, but couldn't you just set up a calender alert using Evolution?

---

### Post by acreech on 2009-07-13
> **kindofblue89 said:**
> I know this does not answer your question, but couldn't you just set up a calender alert using Evolution?

I want to be able to recieve it from a different computer, such as my work PC. The calendar alert does not send an email, so I wouldn't be able to see the alert. Set up in a cron job it could send an email reminder of upcoming meetings to a group of associates for me. Then I would not have to do it, it would just be done and I would not worry about forgetting to get the notice out to everyone. 

I don't think the alert would do what I want the cron job to do. if it does.... then I don't know how to make the calendar alert to do it.

---

### Post by acreech on 2009-07-14
I would like to know if is possible send a email with evolution from the command-line, without need use a graphic screen for any part of it.

---

### Post by unutbu on 2009-07-14
Perhaps install the bsd-mailx package and then send mail from the command-line with 
```

cat textfile | mailx -s Subject mail@domain.com
```

see [http://ubuntuforums.org/showpost.php?p=7469400&postcount=3](http://ubuntuforums.org/showpost.php?p=7469400&postcount=3)

---

### Post by acreech on 2009-07-14
> **unutbu said:**
> Perhaps install the bsd-mailx package and then send mail from the command-line with 
```

cat textfile | mailx -s Subject mail@domain.com
```

see [http://ubuntuforums.org/showpost.php?p=7469400&postcount=3](http://ubuntuforums.org/showpost.php?p=7469400&postcount=3)

I was hoping to be able to use evolution so that I did not have any issues with distrobution package upgrades. This worked before, I think in Festy Fawn, but after the upgrade to Gutsy Gibbon it quit working. I was using Sendmail at that time. so I figured if I could get it to work though evolution it would withstand the upgrades. 

Thanks for the suggestion though. I will look into it. I also wondered if Sawfish could send keystrokes to finish the GUI and if the cron Job could control sawfish to tell it to send the keystrokes.

---

### Post by acreech on 2009-07-21
You can actually compose that message in a text file and then save it to the outbox of evolution. It will pick it up and mail it.

---

### Post by gigahz on 2009-09-15
> **michy99 said:**
> That's a bit of overkill for a command to attach to a hotkey, which is what he asked for.

Not overkill at all. I just found out how to send an image with evolution from command line! (from jbrout actually)

Can I somehow specify more than one image? (A filelist to be attached)

best
arnotixe

---

### Post by gigahz on 2009-09-15
> **unutbu said:**
> Perhaps install the bsd-mailx package and then send mail from the command-line with 
```

cat textfile | mailx -s Subject mail@domain.com
```

see [http://ubuntuforums.org/showpost.php?p=7469400&postcount=3](http://ubuntuforums.org/showpost.php?p=7469400&postcount=3)

... and if you want to treat INCOMING emails automatically you should have a look at mailagent. That rocks! I've done very cool things with mailagent :)

hint: Does your cofee brewer read it's email? It could with mailagent :)

---

### Post by ram4 on 2009-09-15
> **gigahz said:**
> ... and if you want to treat INCOMING emails automatically you should have a look at mailagent. That rocks! I've done very cool things with mailagent :)

hint: Does your cofee brewer read it's email? It could with mailagent :)

Absolutely, so did I :) (do very cool things with mailagent).  And I still do, although my rules are no longer the most complex ones in the galaxy.  I've been outsmarted by the Debian maintainer of the mailagent .deb, who is truly doing **amazing** things.

I never felt compelled to add coffee brewer reading abilities though. :lolflag:  Maybe in another life.

-- Raphael

---

