---
title: "Comcast Email Does Not Work with Ubuntu"
date: 2010-07-06
forum: General Help
---

### Post by lesh1 on 2010-07-06
HELP!

This is my first Ubuntu installation, and I sure like its efficiency and speed.

But I can't get access to my Comcast email no matter what I try.  I've spent 3 days on this, reading everything I can find, trying all  kinds of "solutions," all to no avail.

I'm hoping someone here can help.

Comcast email doesn't work, either through Smartzone webmail, or  using an email program like Thunderbird or Evolution.  All other email  (Yahoo, Google) works fine.  But not Comcast.
 
I have managed to get Thunderbird to send  emails, but neither it nor anything else receives emails. 
Using Thunderbird: when  trying to login to receive emails with Thunderbird, I get "Host  Contacted, sending login information" and then after an extended delay  get an error message: "Sending of password did not succeed.  Mail server  [mail.comcast.net]("http://mail.comcast.net/") responded: invalid  username/password".
 
However, my username and password that  I'm entering are correct (they work with a Windows computer and  Thunderbird Windows).
 
I've tried every combination of  setup settings suggested by Comcast, and by others (there are lots of  combinations), and nothing works.
 
With SmartZone, I get  the login screen and can enter my username and password, but then the  screen just freezes with a blank.  I've tried clearing cache, cookies,  you name it, and it still doesn't work.
 
Is there any way to solve this problem that will drive me away from Ubuntu?  I'd appreciate any  suggestions.  Thanks for your input. 
Les

---

### Post by ac7ss on 2010-07-06
I have had a similar trouble. Go to the [flash test site]("http://www.adobe.com/software/flash/about/") and test your version of flash. 

If it is showing version 9, you will need to update it. Search this site for detailed instructions.

If it is showing 10.0 or 10.1, test your [java runtime version]("http://www.javatester.org/version.html"). Ubuntu 10.4 no longer uses the Sun Java set but now uses an open JRL.

Ensure that your add ons are working properly. Close all browsers when you update versions. un-install old versions before installing new ones if you have troubles. It won't hurt to re-boot between un-install/installs, but is not necessary.

---

### Post by exploder on 2010-07-06
> I have managed to get Thunderbird to send emails, but neither it nor anything else receives emails.
Using Thunderbird: when trying to login to receive emails with Thunderbird, I get "Host Contacted, sending login information" and then after an extended delay get an error message: "Sending of password did not succeed. Mail server mail.comcast.net responded: invalid username/password".

In Thunderbird turn off "use secure authentication" in Server Settings and edit Outgoing Server the same way and you will be able to send and receive mail again.

---

### Post by lesh1 on 2010-07-06
Exploder:

Thanks for your input.  My Ubuntu Thunderbird does not have a choice for "use secure authentication" in Server Settings.  In Edit, Account Settings, Server Settings, it allows me to choose "Connection Security, None" and "Authentication Method, Password, Transmitted Insecurely."  Are these the settings you suggest?  I tried them, in both Server Settings and Outgoing Server and still get the same error message when trying to retrieve email: "Sending of password did not succeed. Mail server pop3.comcast.net responded: invalid username/password".

---

### Post by lesh1 on 2010-07-06
Thanks for your input, ac7ss.  My flash test says: "You have version 10,1,53,64 installed."  

My Java version shows in pink: "Java version 1.6.0_18".

Re your suggestion to "Ensure that your add ons are working properly," I don't know how to do this.  I see Add Ons but don't see how to test them.

I thought of uninstalling and reinstalling Firefox but can't figure out how to uninstall it.  It doesn't show up in Applications or anywhere else I see to remove it.

Thanks for your help.

Les

---

### Post by lordskid on 2010-07-06
I'm not knowledgeable about comcast. but if it is to test your flash, visit youtube and open any video. if it plays then it works. you can also right-click on the video and then about flash. it will show you your flash version. alternatively go to ss10.evony.com the site requires flash too. it will show you your flash version.

regarging java. visit this site 
  [http://java.com/en/download/installed.jsp?detect=jre&try=1](http://java.com/en/download/installed.jsp?detect=jre&try=1)

if java is installed and working it should show you some info about your system.

> **lesh1 said:**
> Thanks for your input, ac7ss.  My flash test says: "You have version 10,1,53,64 installed."  

My Java version shows in pink: "Java version 1.6.0_18".

Re your suggestion to "Ensure that your add ons are working properly," I don't know how to do this.  I see Add Ons but don't see how to test them.

I thought of uninstalling and reinstalling Firefox but can't figure out how to uninstall it.  It doesn't show up in Applications or anywhere else I see to remove it.

Thanks for your help.

Les

---

### Post by lesh1 on 2010-07-06
Lordskid:

Thanks for your help.

Youtube works and Evony works.  But Comcast doesn't.

On the Java link, I get a brief countdown, and then this message:
**"Sorry!  We couldn't find the document requested.**

  The file that you requested could not be found on this server. If you  provided the URL, please check to ensure that it is correct."


This looks like a link problem to me, but maybe I'm wrong.  Does it work at this time for you?  Or is there another test site for Java?


Tx,


Les

---

### Post by lesh1 on 2010-07-06
Tried the Java test again and it worked (they must have been maintaining the site earlier this morning).

It says an update is available, but I'm not sure how to install it.

---

### Post by DavePlummer on 2010-07-06
I have used Comcast email with Ubuntu, with three different email client and Web mail clients for three years with no problems.

---

### Post by lesh1 on 2010-07-06
> **DavePlummer said:**
> I have used Comcast email with Ubuntu, with three different email client and Web mail clients for three years with no problems.

Great, there's hope.  What settings do you use?

Thanks,

Les

---

### Post by richardjr31 on 2011-12-02
it does i found the cure.. :)    In firefox click on tools.......clear resenthistory......check box for clear cookies.   and clear now....and restart browser... that will fix comcast email.....from there to ensure it doesn't happen again.......go to edit.....preferences.....privacy.......accept cookies till i close firefox.   AFTER THAT THE OPTIONS ARE WHAT YOU WANT TO DO. :) IT WORKES PERFECT :)

---

### Post by richardjr31 on 2011-12-02
It worked here with both computers hope so with you too. Damn cookies :)

---

