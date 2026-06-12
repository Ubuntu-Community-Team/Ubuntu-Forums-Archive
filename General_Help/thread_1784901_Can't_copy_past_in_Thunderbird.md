---
title: "Can't copy/ past in Thunderbird"
date: 2011-06-17
forum: General Help
---

### Post by ClientAlive on 2011-06-17
Hi,

I'm running Thunderbird 3.1.10; and, for some reason, can not copy/ paste into the body of the email. This is a real inconvenience and I need to get it sorted out. Does anyone know how to fix this?

Thanks in advance for your help.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
more details it works for me 
thunderbird 3.1.10
ubuntu 10.04.2

---

### Post by ClientAlive on 2011-06-17
> **pqwoerituytrueiwoq said:**
> more details it works for me 
thunderbird 3.1.10
ubuntu 10.04.2


I'm not sure I know details to give you. I get the suspicion I'd made some selection in edit > preferences but have been over every inch of that thing over and over again and can't find anything to change that would fix the problem.

About the only details I would know to give you are details about my system but I'm not sure that's what would help. I'll list them anyhow though. If you have anything specific you need to know let me know and I'll give it.

Thanks.

* Ubutntu 10.04 LTS
* Had this thing called "mail-notification-evolution" installed but removed it yesterday because it never worked right.
* That "mail-notification-evolution" thing would also install "mail-notification" so there would be both of them after you just installed the one. When I removed it (complete removal) they both were removed.
* Have "standard plugins for Evolution" installed right now

And the copy/ paste thing has never worked for me. I've just put up with it until now. One of the settings I did in edit > preferences, right after I first installed it and was configuring and adding accounts, was to make email plain text only; but, in my experience, it doesn't seem to stick to it anyway. I wouldn't think that would make copy/ paste not work though.

That's about all I can think of right now. If you have any questions let me know.

Thanks.

---

### Post by ajgreeny on 2011-06-17
Not wishing to state the obvious, but I presume you realise that you can only edit/copy/paste into new messages that you are writing.

You can not add or delete or copy anything into those you have received from others, or are simply viewing in the message pane.  If you have messages saved in drafts, you need to open them for editing in a new window to be able to edit them.

If you want to use someone else's message as a template to send elsewhere you can highlight it and go to Message->Edit message as new and then paste etc etc as you want.

Apologies if you are aware of this already, but it would not be the first time that someone has tried to edit a message they have received or are simply viewing without opening it properly.

---

### Post by ClientAlive on 2011-06-17
> **ajgreeny said:**
> Not wishing to state the obvious, but I presume you realise that you can only edit/copy/paste into new messages that you are writing.

You can not add or delete or copy anything into those you have received from others, or are simply viewing in the message pane.  If you have messages saved in drafts, you need to open them for editing in a new window to be able to edit them.

If you want to use someone else's message as a template to send elsewhere you can highlight it and go to Message->Edit message as new and then paste etc etc as you want.

Apologies if you are aware of this already, but it would not be the first time that someone has tried to edit a message they have received or are simply viewing without opening it properly.


Thank you ajgreeny. Yes, I understand. I am talking about new outgoing emails or replies to emails where I am writing the reply. Since the day I installed Thuderbird I've been unable to paste into the message. When I've wanted to include a url or take text from another document I had saved I have to have both windows open next to one another and physically type the content into the email. The clipboard is working fine as it is possible to paste content into a new document or anywhere else but the email.

I'm at a total loss and I already have a considerable investment of time into setting this thing up (3 accounts, an entire directory structure of folders with received emails placed in them, etc).

I'd sure love to find a way to get this fixed.

---

### Post by ajgreeny on 2011-06-18
> **ClientAlive said:**
> Thank you ajgreeny. Yes, I understand. I am talking about new outgoing emails or replies to emails where I am writing the reply. Since the day I installed Thuderbird I've been unable to paste into the message. When I've wanted to include a url or take text from another document I had saved I have to have both windows open next to one another and physically type the content into the email. The clipboard is working fine as it is possible to paste content into a new document or anywhere else but the email.

I'm at a total loss and I already have a considerable investment of time into setting this thing up (3 accounts, an entire directory structure of folders with received emails placed in them, etc).

I'd sure love to find a way to get this fixed.
That seems very strange.  have you set your email messages to be written as plain text only, not html?   I am not sure why that should stop you pasting into them, but I am grabbing at straws here.

PS:  Do you use glipper or parcellite clipboard manager?  Again, I don't see why that should make any difference, but...?

---

### Post by ClientAlive on 2011-06-20
> **ajgreeny said:**
> That seems very strange.  have you set your email messages to be written as plain text only, not html?   I am not sure why that should stop you pasting into them, but I am grabbing at straws here.

PS:  Do you use glipper or parcellite clipboard manager?  Again, I don't see why that should make any difference, but...?


Sorry for going mia for a bit there. Just got back from out of state.

Yeah, I had set it to text only. I'll have to try and find that setting again and change it to see what happens.

I just checked in synaptic and neither glipper nor parcellite are installed - so ok there.

I'll try find the setting to change from text only and let you know what happens.
-------------------------

Edit:

Well, I've looked all over for setting it to plain text only and am not seeing anything straightforward/ obviouse in Edit > Preferences. I did notice that the character encoding is set to "Western (IS0 8859-1)" though. I don't know why but I was under the assumption it ought to be ASCII.

I'm stumped here. I really don't want to redo all that work buy reinstalling. Some of it I'm not sure I could save/ transfer back to a fresh install.

---

### Post by ClientAlive on 2011-06-20
I discovered this morn that I can copy/ paste from one email in thunderbird to another. For instance, to copy the body of a previously 'sent' email into the body of a new email. I just can't paste from apps outside of thunderbird into thunderbird emails.

---

### Post by Azdour on 2011-06-21
Hi,

Not sure if this will be of any help. When copying from an external app do you close that app before pasting it into Thunderbird?

I believe when you close an app any clipboard related to it also goes.

---

### Post by ClientAlive on 2011-06-21
> **Azdour said:**
> Hi,

Not sure if this will be of any help. When copying from an external app do you close that app before pasting it into Thunderbird?

I believe when you close an app any clipboard related to it also goes.


Thanks for the tip. No, it isn't that way with text documents anyhow. I don't know about other formats though - maybe it is with them.

I just figured something out about this whole thing (like 2 minutes ago); and, it just happens to be the case, I copy and pasted from a text document, that I had closed before pasting, and it worked.

I had clicked "Write" in the main window and opened up a new email to run a test. I typed in some garbage @gmail.com and entered some more junk into the subject line, then put my cursor in the body of the email. I got to examining what is in the "edit" menu. The edit menu contains the features: cut, copy, paste and a couple others too. One of those others is "paste without formatting."

I noticed that they all remain grayed (inactive) as long as there is nothing on the clipboard. When I did copy text to the clipboard though I gained the option for "paste without formatting" but not "paste." I never get the paste option. I used the feature "copy without formatting," which is ctrl+shift+v, and it worked like a charm.

I'm not certain but it keeps entering my mind that the reason I don't get the "paste" option is because of some security setting. I remember, years ago, a friend of mine who's very tech savvy, telling me that setting your client to receive emails as text only provides security to you. He said that then you don't have to worry about a lot of the junk that can come through in an email and harm you. I don't know if the developers of these apps consider it a "security feature" but I remember I set Thunderbird up that way (to receive email as text only).

Maybe once I find out for sure what's going on with the paste option, if it is the 'text only' thing - maybe I end up deciding to keep it anyway. At least I'll know.

Thanks for all your help guys. I'm gonna mark this one solved. I think - "I got this" now.

Jake

---

