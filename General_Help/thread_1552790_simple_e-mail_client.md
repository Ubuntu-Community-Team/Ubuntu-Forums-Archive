---
title: "simple e-mail client"
date: 2010-08-14
forum: General Help
---

### Post by hernandez14 on 2010-08-14
Hi there,
I'm looking for a simple e-mail client and I can't find anything.

Now I'm using GNUbiff as a mail notifier plus Firefox (webmail -- gmail).
The thing is I have a seven years old computer. As you can imagine it isn't powerful. GNUbiff is great, but Firefox isn't lightweight. Also I can't call myself as webmail fan. It's not comfortable to read new e-mail when firefox is off. I need to wait until it'll start, I have to log in and then I'm able to read new message. It's like using a lorry to grocery shopping to me.

That's why I'm looking for a simple, clean, lightweight and equipped only with essential features and preferably nothing else e-mail client.
All I need is:
* IMAP,
* check two (g)mail accounts (one also would be great),
* read e-mails,
* write e-mails in plain text,
* download attachments,
* nothing else.

I don't even need templates, signatures, an address book, filters... not to mention about PIM stuff. I need nothing, but things listed above.

Actually what I need is GNUbiff plus reading and writing plain text emails. Thunderbird or Evolution is absolutely out of table.

I know I have high expectations, but maybe one of you guys heard about something like that?

---

### Post by DeMus on 2010-08-14
> **hernandez14 said:**
> Hi there,
I'm looking for a simple e-mail client and I can't find anything.

Now I'm using GNUbiff as a mail notifier plus Firefox (webmail -- gmail).
The thing is I have a seven years old computer. As you can imagine it isn't powerful. GNUbiff is great, but Firefox isn't lightweight. Also I can't call myself as webmail fan. It's not comfortable to read new e-mail when firefox is off. I need to wait until it'll start, I have to log in and then I'm able to read new message. It's like using a lorry to grocery shopping to me.

That's why I'm looking for a simple, clean, lightweight and equipped only with essential features and preferably nothing else e-mail client.
All I need is:
* IMAP,
* check two (g)mail accounts (one also would be great),
* read e-mails,
* write e-mails in plain text,
* download attachments,
* nothing else.

I don't even need templates, signatures, an address book, filters... not to mention about PIM stuff. I need nothing, but things listed above.

Actually what I need is GNUbiff plus reading and writing plain text emails. Thunderbird or Evolution is absolutely out of table.

I know I have high expectations, but maybe one of you guys heard about something like that?

I have absolutely no idea if the program you are looking for exists. You say Firefox is not lightweight. No, that's true. It takes for ever to load and showing pages is slow. What you could do, even though you are not a webmail fan, is using Google Chrome. It is lightweight and lightning fast. When you enter your mail webpage after having signed in you can let Chrome remember your password, so the next time you don't need to sign in anymore. It will be done automatically.
If this is not what you like then I wish you good luck finding something else. If you find it, please let us know, so others may benefit from it as well.

---

### Post by DeMus on 2010-08-14
Have a look [_here_]("http://www.junauza.com/2008/07/8-best-e-mail-clients-for-linux.html") and see if Balsa is something for you. They say it is lightweight.

When you type: "**_linux lightweight e-mail client_**" in Google you get many answers.

---

### Post by VCoolio on 2010-08-14
Check [sylpheed](http://sylpheed.sraoss.jp/en/) or [claws-mail](http://www.claws-mail.org/). Really lightweight would be text-based, like mutt or alpine.

---

### Post by wojox on 2010-08-14
+1 for Mutt. I doesn't get anymore lightweight than that.

---

### Post by HermanAB on 2010-08-14
+10 for mutt.  

The little doggy can do everything.  It is good for use on a server.

---

### Post by damnick on 2010-08-14
i'm pretty sure that for imap alpine is better than mutt,
So my vote goes to Alpine.

---

### Post by hernandez14 on 2010-08-27
Thank you guys for your suggestions.

I'm writing only now, because I was testing non-intensively your propositions. In fact I haven't finished testing. You can read below what I've figured out.

**Sylpheed**
It's quite lightweight. Only one thing I can't stand. I don't know how to make Sylpheed to automatically mark as read everything that goes to gMail spam folder. Also I have to check twice e-mails which are automatically by filters put into another folder. I'm checking in IN-BOX and then this same message is still marked as unread in the second folder.

**Claws** has this same marking-as-read problem and it's very similar to Sylpheed, as its fork, but Sylpheed is easier to get started if you have gmail.

**Balsa**
The view is nice and clean, but I can't send e-mails. There is a problem with authentication which is required.

Originally I wanted GUI software, but when I saw how lightweight GUI programs worked I decided to give text-based a chance.

**Mutt**
I wasn't able to configure mutt in less than ten minutes, so I thanked for cooperation and tried...

**Alpine (winner)**
It's great. I used this for a while a few years ago. It was called Pine.
Running alpine with "-i" takes me directly into my in-box, then I can read an e-mail, take an appropriate action (respond, delete or archive) and quit really fast.
_Although my dream is to make Alpine to act exactly like gmail so I'll don't need to clean all the clutter with webmail. I haven't figured out yet how to (A) "archive" mails exactly like gmail does and (B) delete them permanently._
Perhaps (I didn't check) it has the same marking-as-read problem (as Sylpheed), but I don't see other folders in in-box view, thus it's not so annoying.
It would be better to have something like this with GUI, but I finally decided to give Alpine a chance and test it in long-term.

Alpine won my "the simple e-mail client contest" and it works for me as yet, then thank you all guys for you suggestions.

---

### Post by beacon on 2010-09-08
I have downloaded Alpine, and it is on the list of installed programs. But I can't find it. Any suggestions?

---

### Post by oldos2er on 2010-09-08
Alpine is a CLI app, therefore it won't have a menu entry. Open a terminal, ```
alpine
```

---

### Post by beacon on 2010-09-08
Thanks Oldoss2er. You have shown me how to get in, so I'll see if I can set it up.

Regards

---

### Post by oldos2er on 2010-09-08
Maybe this will help: [http://www.washington.edu/pine/tutorial.4/index.html](http://www.washington.edu/pine/tutorial.4/index.html)

Though it says it's for Pine, it should work with Alpine too.

---

### Post by beacon on 2010-09-09
Very helpful indeed. Thanks once again.

---

