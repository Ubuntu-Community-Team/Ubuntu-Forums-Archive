---
title: "Help Getting Serious with Ubuntu"
date: 2006-02-15
forum: General Help
---

### Post by Ingla on 2006-02-15
Hello.

I realize that a lot of people use Linux mostly for non-business purposes. Therefore, it's sometimes hard to get knowledgeable answers about some kinds of programs. However, I really want to be able to function totally under Linux... if it can be done. 

I use the computer heavily for work and have very nice programs for everything I need under Windows. I don't mind the fact that Linux programs work differently and, sometimes, have less cute GUI's, but I need to get all the functions I require under Linux...even if that sometimes requires a couple of extra clicks or commands.

The problem is software. 

One of the main issues is e-mail. 

1. As I run a couple of Web sites, I tend to get a lot of spam. Under Windows, I have a couple of POP3 e-mail checkers which show me everything on the server and allow me to delete e-mails directly from there, without ever downloading them to my machine. One even allows me to bounce messages back to the sender.

I'm having real difficulty finding software like this for Ubuntu. I located one popchecker, but it works from the command line. I was unable to get it to work properly and, anyway, command line is not the way to go with this job... it takes to long to do all this even with a simple click. Using commands for this daily clean up would take hours.

Apparently, kshowmail will do what I want and some people seem to be running it. I can't get a working version. As a newbie (and even if I weren't), I don't want to get involved with poorly documented tar.gz installations. 

I have not found a deb for kshowmail. There are several rpm's available. However, I tried three of them (using alien). The first wouldn't work at all...the system couldn't even find the program. The other two installed it but it wouldn't work. When I tired to check a mail account it returned an error notice "Unknown protocol...POP3. It's a POP3 checker for Heaven's sake. Could be a dependency problem, but apt-get didn't mention it.

If anyone has any advice or, better yet, a deb they've used successfully under Breezy, I 'd certainly appreciate it.

2. I create and send HTML e-mails. I've found no program to do this. Under Windows, I use special software (Groupmail), which not only manages and keeps mailing lists, but allows you to write a plain text message and attach an HTML page. It then creates a multipart message and sends the messages to a separate mail server on my machine for dispatch to the recipients.

Outlook Express is the only e-mail client I know which can take an HTML page and send it as an e-mail. Internet Explorer has a "Send Page" function, but it doesn't produce a nice mail.

I have Evolution and Thunderbird, neither of which seems to be able to do this. Also, Firefox doesn't appear to have such a function.

Does anyone know how I can create HTML e-mails and send them to a list under Ubuntu?

3. It is also a must to be able to run Internet Explorer well. Some sites are written for IE only. This is very bad practice on the part of the developers, but I can't change the world. I haven't tried this yet, but would appreciate some advice. I'm aware of Wine, but hear people have a lot of trouble with it. I haven't checked out Wine or Crossover Office. Advice, please?

3. Antivirus: I realize folks don't feel as threatened under Linux, but I'm sure that, as Linux gains in popularity, this is going to change. I've tried Clam and a couple of others. However, without realtime scanning, they're not good for much. It often is too late to do a virus scan when a machine is already infected. The only things I've found are commercial applications which, for some reason, cost many times what the same company's Windows version sells for. 

Is there a real time virus scanner that can run in the background on Ubuntu?

If anyone can address any or all of these issues, it would be a great help.

Thanks very much.

---

### Post by jamespgray on 2006-02-15
I am pretty much a beginner myself, but I have some suggestions that might help.  

1. In terms of email if you are trying to get rid of spam then Spam Assassin would be a good bet.  Although, it will likely require some setup.

2.  I've just tested that I can send HTML email from Thunderbird for Windows.  I can't imagine that Thunderbird for Linux won't be able to do this also.  I think there is an option somewhere that can force emails to be sent as text so you may need to change that.  (I don't have time at the moment to fireup Ubuntu to check this.)

3.  If you have trouble getting wine to run IE, and I suspect you may.  Given enough memory you can install windows inside Ubuntu using VMware. For me, I find that firefox is good enough to make the sites I visit usable, but not always pretty.  

4. Not sure if they will meet your needs but see clam-av package and [http://www.grisoft.com](http://www.grisoft.com) (they do Linux as well as Windows now).

---

### Post by jannol on 2006-02-15
2. In evolution, create new and then from the menu, choose format > html, then attach > html-file

3. I think the best way so far for installing ie is [http://www.tatanka.com.br/ies4linux/en/instructions](http://www.tatanka.com.br/ies4linux/en/instructions)

---

### Post by nanotube on 2006-02-16
and as to antivirus... there are no viruses for linux in the wild currently, so if you do install a realtime scanning av, all it will be doing is sitting there sucking up your resources, and not doing anything useful. so i really wouldnt worry about that. :)

---

### Post by Ingla on 2006-02-16
Hi.

The HTML e-mails I meant are not the standard format sent by e-mail clients. I was talking about writing an HTML file (a small Web page with images and all) and having the client send that.

Guess what! Thunderbird has an extension to Edit the HTML source. I installed it and voila! :-D 

Anyone who knows HTML and has somewhere to serve images from can create great messages. Worth checking out.

Thanks for all the help.

---

