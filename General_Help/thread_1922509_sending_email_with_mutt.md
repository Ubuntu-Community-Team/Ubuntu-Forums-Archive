---
title: "sending email with mutt"
date: 2012-02-08
forum: General Help
---

### Post by boregard on 2012-02-08
Hi all, I installed mutt today and got it working where I can send myself a test email. Been reading Ubuntu documentation and still confused as to how I can send email to contacts who use yahoo,gmail,ect.If anyone could point me in the right direction it would be greatly appreciated. Regards

---

### Post by marshag63 on 2012-02-09
Hello!

You  will need to edit the muttrc file.

If you want to test drive a working setup with mutt and gmail, try INX linux (cli distro) with a step through on using mutt and gmail. 

I recommend the Lucid version   [http://inx.maincontent.net/devel/unstable/lucid-inx/](http://inx.maincontent.net/devel/unstable/lucid-inx/)

or you could try the 1.1 version - there is even a version for a virtual machine.  Really great distro  [http://inx.maincontent.net/download.html](http://inx.maincontent.net/download.html)

Hope this helps.

mdg

---

### Post by Khayyam on 2012-02-09
boregard ...

if you hit the 'm' key mutt will prompt you for a recipient address. If you've setup 'aliases' you can insert either the alias name or <tab> complete through them.

An example of how your .muttrc might look

```
set alias_format="%2n %t %-10a %r"
set alias_file="~/.mutt/aliases"
source ~/.mutt/aliases
```

Your ~/.mutt/aliases should then look like:

```
alias john John Johnston <johnj@gmail.com>
alias jane Jane Johnston <janej@jmail.com>
```

In mutt's "index" (or main) you can 'alias' (bookmark) an address by typing 'a', mutt will then prompt you for details, by default mutt will use the information provided in the senders headers, and so you can hit return to accept these. The entry will be written to the above defined aliases file.

Also in any view if you type "?" will get the "help" section for that view.

HTH ...

---

### Post by boregard on 2012-02-09
Thanks to all kind replies.I will try all of your suggestions. When I first installed mutt I had no idea it was this complicated.I see now I have a lot more reading & studying to do,lol.I think my first mistake when installing was choosing local instead of something else in the posfix window. Best Regards to all

---

### Post by Khayyam on 2012-02-09
Boregard ...

Your welcome. I would say 'fully featured' rather the 'complicated'. I can have it do my mail archiving (automatically), change headers (reply to, etc) based on the directory I'm currently working in or by the sender (via 'hooks'), search nearly twenty years of mail by string/sender/subject/date, have attatchements converted to be viewed via pager based on mimetype. I can also use my editor of choice to write replies, pass the text through tidy filters, read in the output of commands, etc, etc. I really wouldn't choose to use anything else.

I have changed my setup very little in the nearly twenty years I've been using mutt and so the initial labour has been more than repaid.

best ...

---

### Post by andrew.46 on 2012-02-10
> **boregard said:**
> I think my first mistake when installing was choosing local instead of something else in the posfix window.

Postfix is probably overkill on most home systems. An easier setup would probably use msmtp to send the mail and perhaps fetchmail and procmail to receive and sort the mail. There are many more variations :).

---

