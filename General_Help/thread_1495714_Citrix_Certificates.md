---
title: "Citrix Certificates"
date: 2010-05-28
forum: General Help
---

### Post by tufu5 on 2010-05-28
I just installed Citrix to my computer but when I try to use it I get an error message saying

"You have not chosen to trust "Equifax Secure Global eBusiness CA-1", the issuer of the server's security certificate (SSL error 61)."

So I downloaded the certificates to allow me to use it but I am unable to copy them to the /usr/lib/ICAClient/keystore/cacerts/ directory, I cant download them straight to that folder either. I have administrative privileges but still I cant do anything with the files in those folders other than look at them. Can someone tell me how to put files in those folders?

---

### Post by Dragynn on 2010-09-08
Well this is kinda dated, but just in case anyone else has this problem....

I had the same issue installing the Citrix client in Lucid 10.04, it installed just fine, but was missing a cert for Godaddy of all things. So got the cert and using "sudo mv (filename here)" was able to move it into that directory with no problem, not sure why it wouldn't move for you, but here is a link to another workaround:

[geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex]("geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex")

---

### Post by flyingmule on 2011-05-03
For n00bs like myself, let me amplify Dragynn's excellent suggestion, which with a little experimentation worked great. This BTW was to install a GoDaddy security certificate and rectify Citrix-related SSL error 61 when attempting to install/run ICAClient on Ubuntu 10.04.

What you need to do is:
1) Download the SSL cert from [https://certs.godaddy.com/anonymous/repository.seam]("https://certs.godaddy.com/anonymous/repository.seam") into your Downloads folder (this should happen automatically). I clicked the first link on this page, gd-class2-root.crt .
2) Open terminal window (in Accessories under that Ubuntu-symbol main menu icon thingie at one end of your main toolbar)
3) In the terminal window, type sudo mv /home/[your username, no brackets]/Downloads/gd-class2-root.crt /usr/lib/ICAClient/keystore/cacerts . In my case, the text [your username, no brackets] was replaced with the text flyingmule .
4) Exit terminal window (File/Close Window) and try Citrix again. 

This worked for me - YMMV. Please add enhancements below!

---

### Post by tufu5 on 2011-05-26
I found another way to fix the problem myself

1. Install the Citrix ICA client
2. Go to the Firefox advanced settings in the preferences menu and click view certificates
3. Find the certificate you need (in this case it was equifax secure)
4. Export it to the Citrix Cacerts folder

After this Citrix ran fine without any more error messages

---

