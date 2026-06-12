---
title: "Unable to Validate Certificate After Latest Update"
date: 2010-11-18
forum: General Help
---

### Post by onaridge on 2010-11-18
Just did an auto update. Among the list of things was an SSL update and now I can no longer connect to my MSN account in Pidgeon. I get an error "unable to validate certificate, the certificate for Omega.contacts.msn.com could not be validated. The certificate chain present is invalid."

What do I do?

---

### Post by onaridge on 2010-11-18
Fixed mail issue, still have above issue

---

### Post by nex_gen on 2010-11-18
Hi, I found a solution in this blog:

[http://blog.andreineculau.com/2010/11/pidgin-and-msn-certificate-error-for-omega-contacts-msn-com/]("http://blog.andreineculau.com/2010/11/pidgin-and-msn-certificate-error-for-omega-contacts-msn-com/")

Hope this helps!

---

### Post by ethos_dacapo on 2010-11-18
Solution can be found here: [http://developer.pidgin.im/ticket/12906]("http://developer.pidgin.im/ticket/12906")

How to replace your certficate (the GUI method):

Go to pidgin's Tools->Certificates to remove the old certificate. Don't close this window yet. (You can, but it is easier to not)

With your browser, go to [https://omega.contacts.msn.com](https://omega.contacts.msn.com). It will give you "Directory Listing Denied"

With Firefox, if you click on the lock in the lower right corner, you get a dialog box, where you can click on View Certificate. On its Details tab, you can export the certificate to a file.

Now, back on the pidgin Tools->Certificates dialog, you can add this certificate, and all is well.

When I click on the lock in the address bar in IE, I can see the certificate, but it won't let me export it, so I can't help you there.

---

### Post by onaridge on 2010-11-18
I didn't see the 2nd message so used the first message method. I just copied and pasted the new cert and overwrote the old one. I think it worked. Thanks guys!

---

### Post by eMKey on 2010-11-18
> **ethos_dacapo said:**
> 

How to replace your certficate (the GUI method):

Go to pidgin's Tools->Certificates to remove the old certificate. Don't close this window yet. (You can, but it is easier to not)

With your browser, go to [https://omega.contacts.msn.com](https://omega.contacts.msn.com). It will give you "Directory Listing Denied"

With Firefox, if you click on the lock in the lower right corner, you get a dialog box, where you can click on View Certificate. On its Details tab, you can export the certificate to a file.

Now, back on the pidgin Tools->Certificates dialog, you can add this certificate, and all is well.


+1 
It worked for me. Thanks.

---

### Post by Skabeh on 2010-11-19
Thanks Working goood :popcorn:

---

### Post by magiceffects on 2010-11-19
I tried the first method and it worked without any issues but everytime I add a new contact to my list I am faced with the problem again and have to edit that file again. Is there a method that fixes the problem without it coming back when new contacts are added??

I am going to try the second method now, although I have a strong feeling once another contact is added I will have the same problem again... I will repost once this is confirmed; in the meantime, does anyone have any ideas? :)

---

### Post by magiceffects on 2010-11-19
> **magiceffects said:**
> I tried the first method and it worked without any issues but everytime I add a new contact to my list I am faced with the problem again and have to edit that file again. Is there a method that fixes the problem without it coming back when new contacts are added??

I am going to try the second method now, although I have a strong feeling once another contact is added I will have the same problem again... I will repost once this is confirmed; in the meantime, does anyone have any ideas? :)

Added a contact since doing method two; with no issues so far... although, the contact I added did not receive a confirmation request and in turn had to add my address to their contact list.

[The Day After]:

Once again getting the same error. I do not know know why this has been marked as SOLVED. It's a temporary fix imo.

---

### Post by claracc on 2010-11-20
The fix posted in this link [http://www.webupd8.org/2010/11/fix-pidgin-msn-omegacontactsmsncom.html#disqus_thread](http://www.webupd8.org/2010/11/fix-pidgin-msn-omegacontactsmsncom.html#disqus_thread) has solved the problem for me.

---

### Post by Soul-Sing on 2010-11-20
ethos_dacapo thank you, it worked.

---

### Post by Matti L on 2010-11-20
> **claracc said:**
> The fix posted in this link [http://www.webupd8.org/2010/11/fix-pidgin-msn-omegacontactsmsncom.html#disqus_thread](http://www.webupd8.org/2010/11/fix-pidgin-msn-omegacontactsmsncom.html#disqus_thread) has solved the problem for me.
I used this method and it worked but probably their all the same fix. Tnx!

EDIT: didn't work for long. LAME!

---

### Post by Soul-Sing on 2010-11-20
> **Matti L said:**
> I used this method and it worked but probably their all the same fix. Tnx!

EDIT: didn't work for long. LAME!

AFAIK the certificates are changed again this day, they are SSL certificates, if you have trouble connecting  via SSL disable SSL if possible for the time being.
The latest certificate is working fine here.
( [http://blog.andreineculau.com/2010/1...tacts-msn-com/](http://blog.andreineculau.com/2010/1...tacts-msn-com/))

---

### Post by onaridge on 2010-11-20
This is nuts...why do they keep changing the certificates?

---

### Post by Artemis3 on 2010-11-21
The solution to this is here: [http://developer.pidgin.im/wiki/MSNCertIssue](http://developer.pidgin.im/wiki/MSNCertIssue)

Manually updating the certificate will only get you so far, you need to add those new intermediate certificates.

---

### Post by claracc on 2010-11-21
Thankyou Artemis3, the fix you suggest works, but I had to delete my  omega.msn.contacts certificate in pidgin and add the two intermediate certificates in [http://developer.pidgin.im/wiki/MSNCertIssue](http://developer.pidgin.im/wiki/MSNCertIssue)

The fix I posted yesterday > claracc 	
Re: Unable to Validate Certificate After Latest Update
The fix posted in this link [http://www.webupd8.org/2010/11/fix-p...#disqus_thread](http://www.webupd8.org/2010/11/fix-p...#disqus_thread) has solved the problem for me.
1 Day Ago 12:57 PM, no longer works.

Why is it?

---

### Post by Matti L on 2010-11-21
Windows Live Messenger has a new version with Facebook and other social stuff so maybe those changes cause these Pidgin problems. Hope Pidgin gets a new version soon.

Oh, and it seems that the fix I used yesterday works on every other time I start Pidgin and then other times doesn't work.

---

### Post by onaridge on 2010-11-21
How do you save the two files? I can't open them to save them.

---

