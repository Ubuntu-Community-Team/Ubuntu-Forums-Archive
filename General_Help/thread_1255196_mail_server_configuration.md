---
title: "mail server configuration"
date: 2009-09-01
forum: General Help
---

### Post by LgLindstrom on 2009-09-01
Hi
I have a number of mail accounts, hotmail, gmail, company mail, Internet provider mail.

I would like to setup a mail server, which fetches mail from all my accounts. Then I should be able to connect to this mail server using a GUI client or a Web Client. (it would be nice if I could do the same with calendar and tasks)

Is this possible,, and how (which components)

//newbe
//lasse

---

### Post by thinkdez on 2009-09-01
You have a few options here.  One you could use a program like [Xuheki]("http://www.xuheki.com/")  This mail client allows you grab mail from multiple accounts.

Or you could set up a local mail server with a webmail client and use fetchmail to grab mail from multiple accounts.  I am currently using this method for my setup.  
Components you need would be:
      - a mail daemon [I am using postfix but you can use whatever you prefer]
      - an IMAP/POP daemon [Again your choice but I used courier for this]
      - fetchmail [used to grab mail from external accounts
      - webmail client [I use horde as it has calendar functions as well]  

Note: for the webmail client you will also need apache.  You can use another client like evolution, thunderbird etc to check your mail from the server.

There are numerous options and tutorials online about this.  I used [this one]("http://flurdy.com/docs/postfix/") with some of my own modifications to it. 

Have fun!

---

### Post by LgLindstrom on 2009-09-02
Tanks,,, now my evening will be full... :)
//lg

---

