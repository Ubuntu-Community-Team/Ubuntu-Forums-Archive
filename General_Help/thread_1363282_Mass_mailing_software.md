---
title: "Mass mailing software"
date: 2009-12-24
forum: General Help
---

### Post by sangi on 2009-12-24
I am searching for a mass mailing software. I don't wish to use the bcc option in thunderbird. The recipient should see only his email id in the TO area. And each recipient's name should be visible in the text area of the mail (personalised mail). Ever since I switched over from Win (few months ago), I have been trying to find a suitable software in Ubuntu but have so far been unsuccessful in my search. Have tried searching in Synaptic. Could not find. I can use mail merge feature in openoffice but that takes a very long time to send out the mails. Currently, I am using the 'mail merge' add-on to thunderbird. But I cannot personalise the mails with this. Can anyone help me in locating a suitable software?

I am a part of a professional group where we circulate our position lists by email to each other (only to those who wish to receive) on a daily basis. This is purely legitimate use and is not considered spamming.

Since I am a newbie to Ubuntu, please give step-by-step instructions.

Thanks in advance.

---

### Post by s.fox on 2009-12-24
Hello,

At work we have recently taken to using [mailchip]("http://www.mailchimp.com/") to do bulk emailing to existing clients.  Its an online solution and does offer a free version which suits out needs well.  It has some nice video how to's also.

Hope this helps you.

-Silver Fox

---

### Post by sangi on 2009-12-26
> **Silver_fox_ said:**
> 

At work we have recently taken to using [mailchip]("http://www.mailchimp.com/") to do bulk emailing to existing clients.  Its an online solution and does offer a free version which suits out needs well.
-Silver Fox

Yes. I checked it out but it limits to 500 subscribers per user and 3000 mails per month. My requirement is much more - in the region of 1600 subscribers and about once or twice a day. Any other solution please!

---

### Post by lostinxlation on 2009-12-26
A simple script should be able to do the job.
Ask someone who know how to write a script for details.
 
Here is some idea.
 
 
#/bin/csh
 
foreach tmp {`cat recipient.list`)
  set addr = `echo $tmp | sed -e 's/:.*$//'`
  set name = `echo $tmp | sed -e 's/^.*://'`
  sed -e 's/ZZZ/$name/g' mail_content | mail $addr
end
 
 
 
Recipient.list should be like
 
[EMAIL="john@zzz.com:John"]john@zzz.com:John[/EMAIL]
[EMAIL="Jane@qqq.org:Jane"]Jane@qqq.org:Jane[/EMAIL]
[EMAIL="bill@ccc.com:Bill"]bill@ccc.com:Bill[/EMAIL]
......
 
Mail content file should be like
 
 
Dear ZZZ
 
We are pleased to announce......
.....
....
..

---

