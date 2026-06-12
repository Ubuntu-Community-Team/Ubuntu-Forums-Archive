---
title: "Seting up network printing"
date: 2009-11-22
forum: General Help
---

### Post by Spiritof76 on 2009-11-22
I just installed Karmic Server, and run Karmic Desktop an another PC.. I moved my printer to the Server, and I would like access to it from the rest of my home network. I was able to print out from the server, and I can call up the web web anministrator  see the printer, Unfortunately I can't get my local cups from my desktop machine to see the printer. 

To make maters worse while I was poking around in the, I checked off "Use Kerberos authentication"  now when I go to make changes it gives me an error message:```

"Enter your username and password or the root username and password to
 access this page. If you are using Kerberos authentication, make sure you
 have a valid Kerberos ticket."
```
So I need to get this Kerbos thing shut off and get my desktop cups client to see the server cups.

---

### Post by Spiritof76 on 2009-11-22
Bump. Can anyone help? or am in big trouble?

---

### Post by lehkost on 2009-11-22
You can always try unloading printer-related applications and re-loading them from the repository to attempt a return to default settings?

Sometimes, if I have trouble locating a network printer, I manually enter the IP.  If it's connected to the server, as you said, and you're having no problem communicating between the two computers, make sure that you have your printer set up to share.

---

### Post by Spiritof76 on 2009-11-22
Thanks,
I selected this Kerberos selection and I cnt configure it from my webbrowser anymore. So I would like to turn off the Kerberos stuff.. I don't know how to share the printer.

---

### Post by Spiritof76 on 2009-11-22
I got it working: 
I by mucking around I made it worse by activating the kerberos from the administration page, poking around though I found that when I wrote to Use Kerberos authentication it made the file unavaiable to the configurator.  I looked into /etc/cups and found cupsd.conf.O as well as the original cupsd.conf file. I renamed the files so I had my old cupsd.conf back.  

I was back into my original situation. I could print from the server, but I still couldn't print from my desktop.  What I hadn't realized is that  is that I have the same configurator locally. 
put into my browser:Show printers shared by other systems
[http://localhost:631/admin](http://localhost:631/admin)
Checked off "Show printers shared by other systems" when I went to look for the printers Shazzaaam it was there. Printed my browser screen an it was all there.  

I would love to see some clear instructions in non geek on how to activate a server printer from a desktop. Until then I hope my experiance might help anyone who might run into the same situation.

---

### Post by libssd on 2010-06-12
Not Kerberos-related, but I just installed 10.04, and none of my CUPS-accessible printers was visible. By default, apparently "Show printers shared by other systems" is turned off in 10.04.

**Solution**: Printing > Server > Settings  then check the box for "Show printers shared by other systems."

---

