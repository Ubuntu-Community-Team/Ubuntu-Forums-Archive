---
title: "Citrix Receiver 11 and that error 61 &quot;not trusted certs.&quot;"
date: 2011-03-22
forum: General Help
---

### Post by foggys916 on 2011-03-22
Hi,

Have extensively Googled and searched on here, but with no success.

We have a MYPC service at our company, but our support staff have been well trained in the phrase..."we do not offer support for Linux", but the MYPC service that we have did work recently under Ubuntu 9.04 that I had at home, however since upgrading both my laptop and desktop to 10.10 and 10.4 respectively, neither now work when I use the Citrix 11 Receiver client.

I get; "You have not chosen to trust "GeoTrust Global CA", the issuer of the server's security certificate (SSL error 61."

So I got, what I thought were the relevant certificates from [http://www.geotrust.com/resources/root-certificates/index.html](http://www.geotrust.com/resources/root-certificates/index.html) (see image for a list of certificates) but still no joy. whilst I don't want to call my support department, I wonder if they have taken a conscious decision to block access to the MYPC system from anything other than Windows OSs?

Any help would be great.

Steve

---

### Post by foggys916 on 2011-03-22
Ah.....

Now realsed that I was not saving the certificates into the /usr/lib/ICAClient/keystore/cacerts folder as I was doing this under user privileges, and not root. Did the same, under root (remembering to change .cer to .crt), and it now works.

Stand down all!!!

> **foggys916 said:**
> Hi,

Have extensively Googled and searched on here, but with no success.

We have a MYPC service at our company, but our support staff have been well trained in the phrase..."we do not offer support for Linux", but the MYPC service that we have did work recently under Ubuntu 9.04 that I had at home, however since upgrading both my laptop and desktop to 10.10 and 10.4 respectively, neither now work when I use the Citrix 11 Receiver client.

I get; "You have not chosen to trust "GeoTrust Global CA", the issuer of the server's security certificate (SSL error 61."

So I got, what I thought were the relevant certificates from [http://www.geotrust.com/resources/root-certificates/index.html](http://www.geotrust.com/resources/root-certificates/index.html) (see image for a list of certificates) but still no joy. whilst I don't want to call my support department, I wonder if they have taken a conscious decision to block access to the MYPC system from anything other than Windows OSs?

Any help would be great.

Steve

---

### Post by v.d.merwe@gmail.com on 2011-04-01
Assuming you have Mozilla Firefox installed, this should work (usual - backup the target directory if you want)

sudo cp /usr/share/ca-certificates/mozilla/*.*  /usr/lib/ICAClient/keystore/cacerts/ 

Did the trick perfectly...

---

### Post by KB8NO on 2011-04-18
My Citrix desktop from work abruptly stopped working in Firefox & Ubuntu 10.10 midday Tuesday 4/12/11 with the same error 61.  Others using Firefox had the same problem at the same time.  I can only imagine that some update in Ubuntu or on the Citrix farm at work changed something.  In my particular configuration the following command in the terminal fixed it immediately.  

sudo cp /usr/share/ca-certificates/mozilla/*.* /home/<myusername>/ICAClient/linuxx86/keystore/cacerts/ 

Thanks for the help.

---

### Post by malapradej on 2011-08-04
Did the trick for me too. I think that most of us assume that if we are accessing the works intranet through our browser, it is the browsers certificates that are needed. But no, Cirtix ICAClient looks in a different folder for these certificates. thus /usr/lib/ICAClient/keystore/cacerts/;

It does not help to set things in Firefox, you need to copy them over from the Mozilla folder to the folder that Citrix is looking for certificates.

After many hours at it the solution it is clear. Thanks guys.

---

### Post by greetp on 2011-12-19
Hello

I've used this solution before & it worked a treat !

However after a rebuild to Lubuntu 11.10, I'm now getting the same error 61 not trusted certs, but with [http://www.valicert.com/](http://www.valicert.com/)

The Citrix Receiver is installed, however I had to manually create /usr/lib/ICAClient/keystore/cacerts/ folders.

I have copied over all the crt files over from the Mozilla folder, but still no luck.

Grateful for any help.

Phili_G (Linux newbie)

---

### Post by HouTex on 2011-12-27
> **v.d.merwe@gmail.com said:**
> Assuming you have Mozilla Firefox installed, this should work (usual - backup the target directory if you want)

sudo cp /usr/share/ca-certificates/mozilla/*.*  /usr/lib/ICAClient/keystore/cacerts/ 

Did the trick perfectly...


I had the same problem and this solved it.  Thanks for posting.

---

### Post by kevdog on 2012-01-12
> **greetp said:**
> Hello

I've used this solution before & it worked a treat !

However after a rebuild to Lubuntu 11.10, I'm now getting the same error 61 not trusted certs, but with [http://www.valicert.com/](http://www.valicert.com/)

The Citrix Receiver is installed, however I had to manually create /usr/lib/ICAClient/keystore/cacerts/ folders.

I have copied over all the crt files over from the Mozilla folder, but still no luck.

Grateful for any help.

Phili_G (Linux newbie)

I had the same experiece as you but found that my citrix client was installed in the /opt directory rather than the /usr directory.  I have no idea why the package manager installed it in this location.  However the correct command for me to get everything up and running was this:

sudo cp /usr/share/ca-certificates/mozilla/*.* /opt/Citrix/ICAClient/keystore/cacerts/

---

### Post by sharkey77 on 2012-05-04
Using the Opt folder worked for me too.  Thank you.

---

### Post by jvdurme on 2012-10-19
Thanks a lot for the /opt folder thing. I was pulling my hair out.
Isn't /opt a Mac folder?

---

