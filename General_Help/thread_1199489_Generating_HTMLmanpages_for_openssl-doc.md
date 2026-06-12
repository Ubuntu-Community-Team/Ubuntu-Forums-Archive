---
title: "Generating HTML/manpages for openssl-doc"
date: 2009-06-29
forum: General Help
---

### Post by trojanfoe on 2009-06-29
Hi there, I want access to more openssl documentation so I installed openssl-doc (which is delivered as .pod files - perldoc format).  I ran 'make' in /usr/share/doc/openssl-doc/doc but I get an error about openssl.pod being missing.  Can anyone tell me how I'm supposed to use these .pod files?  I would ideally like to generate HTML (using podhtml).

Cheers,
Andy

---

### Post by t4thfavor on 2009-06-29
README file under the above mentioned folder/doc has a link to PDF Documentation for openssl, README stands for Read Me.

Maybe I should read the README, thats for SSLeay. From what I gather POD stands for plan old document. They appear to be text files in disguise. I bet you can find a way to wrap html around them in short order.

And finally
[http://blogs.techrepublic.com.com/howdoi/?p=114](http://blogs.techrepublic.com.com/howdoi/?p=114)

---

### Post by trojanfoe on 2009-06-30
Thanks for the reply.  I don't see the link in the README:

```

 apps/openssl.pod .... Documentation of OpenSSL `openssl' command
 crypto/crypto.pod ... Documentation of OpenSSL crypto.h+libcrypto.a
 ssl/ssl.pod ......... Documentation of OpenSSL ssl.h+libssl.a
 openssl.txt ......... Assembled documentation files for OpenSSL [not final]
 ssleay.txt .......... Assembled documentation of ancestor SSLeay [obsolete]
 standards.txt ....... Assembled pointers to standards, RFCs or internet drafts
                       that are related to OpenSSL.

 An archive of HTML documents for the SSLeay library is available from
 http://www.columbia.edu/~ariel/ssleay/

```

The documentation for SSLeay is different to openssl.  There are several conversion programs available named pod2XXX where XXX is man, html, etc. but the Makefile used to generate the manpages from the pod files fails due to missing openssl.pod.

I know that README stands for 'Read Me' and I did read the file before posting - why did you mention that?

---

