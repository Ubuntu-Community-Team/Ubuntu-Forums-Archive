---
title: "Thunderbird shows 2 Outboxes-Local Folders"
date: 2011-02-09
forum: General Help
---

### Post by SuperFreak on 2011-02-09
I have lived with this for months and it isn't a big deal, but my Thunderbird 3.1.7 shows 2 Outboxes-Local Folders. Right now I have my Inbox divided into Local Folders and *****@Sympatico.ca. I would like to put everything under Local folders but I am unsure if I should do this when there are 2 Outboxes

---

### Post by Habitual on 2011-02-09
ah, I was hoping you wanted to remove "Local Folders" which can be done and does eliminate the "duplicates".

---

### Post by SuperFreak on 2011-02-09
I am not sure if this is the reason I have 2 Outboxes in Local folders but I notice mention of Outbox and Outbox.msf twice; the files appear in /home/david/.thunderbird/b12yg7fj.default/Mail/Local Folders and in /home/david/.thunderbird/b12yg7fj.default/Mail/smart mailboxes.

---

### Post by SuperFreak on 2011-02-09
OK I'll bite,

How do I remove Local Folders?  Right now all my archived folders and email for the last 10 years are in Local folders. Also as I said there are two Outbox folders in Local folders (and no Outbox folder in my main identity folder (which contains: Inbox, Drafts, Sent, Archives, Junk and Trash)). Right now all my mail goes to the Inbox of my main identity and I archive in Local Folders. I think it's messed up this way but I don't know how to straighten it out.

---

### Post by Habitual on 2011-02-09
Sorry, I will not give you instructions that could possibly delete 10 years of email and it only works on IMAP.

I have to sleep at night.

Is this a BETA of Tbird, or Natty or both?
```
thunderbird -v
```

You seem to have 2 profiles in Thunderbird. One of them has to go.

**BEFORE** you do anything to profile(s). Exit Thunderbird...
```
cp ~/.thunderbird ~/.thunderbird.org
```

then play with profiles/settings *in* thunderbird.

To restore the copy: Exit Thunderbird...
```
cp ~/.thunderbird.org ~/.thunderbird
```

---

### Post by SuperFreak on 2011-02-09
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.13) Gecko/20101208 Lightning/1.0b2 Thunderbird/3.1.7

I don't think it is beta version see above.

Not quite sure what you mean by "play around with profiles/settings"

Is the cp a command to backup my emails and settings?

---

### Post by Habitual on 2011-02-09
> **SuperFreak said:**
> Is the cp a command to backup my emails and settings?

It is exactly that.

---

### Post by Habitual on 2011-02-09
> **SuperFreak said:**
> Not quite sure what you mean by "play around with profiles/settings"

In Thunderbird --> Edit Menu --> Account Settings --> Copies and Folders
you can 'tell' Thunderbird which copy of any of the duplicate folders you want to use.

The contents of the "other" ones can be dragged to the same desired location.

Good luck.

---

### Post by SuperFreak on 2011-02-09
I am getting the reponse to the copy command :cp: omitting directory `/home/david/.thunderbird'.
I am not able to find any instance of .thunderbird.org in my home folder so I am unsure it has been backed up.
I tried replacing "~" with the directory .thunderbird is in (Home folder) but it had the same result

---

### Post by Habitual on 2011-02-09
> **SuperFreak said:**
> I am getting the reponse to the copy command :cp: omitting directory `/home/david/.thunderbird'.
I am not able to find any instance of .thunderbird.org in my home folder so I am unsure it has been backed up.
I tried replacing "~" with the directory .thunderbird is in (Home folder) but it had the same result

```
cp -pr /home/david/.thunderbird /home/david/.thunderbird.org
```
copies.

```
cp -pr /home/david/.thunderbird.org /home/david/.thunderbird
```
restores that copy.

I forgot the "**-pr**".
-pr is permissions and recursive.

Sorry about that.

---

### Post by SuperFreak on 2011-02-09
Thanks for the clarification it worked this time.

---

### Post by Habitual on 2011-02-09
You're welcome.

Glad it's working out.

---

