---
title: "sendEmail: &quot;smtp.google.com returned a zero-byte response to our query&quot;"
date: 2009-07-09
forum: General Help
---

### Post by t0p on 2009-07-09
I need a command-line email client that I can use in a script.  I also need it to use google's smtp server.  So I figured I'd give [**sendEmail**]("http://caspian.dotconf.net/menu/Software/SendEmail/") a go.  But it won't work!  This is what's happening:

```
t0p@machine:~/Desktop/sendEmail-v1.55$ ./sendEmail -f xxxx@gmail.com -t xxxxx@gmail.com -s smtp.google.com -xu xxxx@gmail.com -xp xxxxxxxxx -u Test -m This is a test of SendEmail
Jul 10 02:26:34 machine sendEmail[9871]: ERROR => smtp.google.com:25 returned a zero byte response to our query.

```

If I specify my gmail username (the -xu flag) as xxxx rather than [email]xxxx@gmail.com[/email], the response is slightly different:

```
t0p@machine:~/Desktop/sendEmail-v1.55$ ./sendEmail -f xxxx@gmail.com -t xxxxx@gmail.com -s smtp.google.com -xu xxxx -xp xxxxxxxxx -u Test -m This is a test of SendEmail
Jul 10 03:04:52 machine sendEmail[10674]: NOTICE => Authentication not supported by the remote SMTP server!
Jul 10 03:04:52 machine sendEmail[10674]: ERROR => smtp.google.com:25 returned a zero byte response to our query.

```

and if I specify port 25 on smtp.google.com, it's like so:

```
t0p@machine:~/Desktop/sendEmail-v1.55$ ./sendEmail -f xxxx@gmail.com -t xxxxx@gmail.com -s smtp.google.com:25 -xu xxxx -xp xxxxxxxxx -u Test -m This is a test of sendEmail
Jul 10 02:57:28 machine sendEmail[10525]: NOTICE => Authentication not supported by the remote SMTP server!
Jul 10 02:57:29 machine sendEmail[10525]: WARNING => The recipient <xxxxx@gmail.com> was rejected by the mail server, error follows:
Jul 10 02:57:29 machine sendEmail[10525]: WARNING => Received: 	550 5.7.1 <xxxxx@gmail.com>... Relaying denied
Jul 10 02:57:29 machine sendEmail[10525]: ERROR => Exiting. No recipients were accepted for delivery by the mail server.

```

Can anyone suggest why sendEmail doesn't want to work?  And if it just can't, can someone suggest a command-line mail program I can use in a script that *will* work with a gmail smtp server?

---

### Post by t4thfavor on 2009-07-09
smtp.gmail.com:587, using tls encryption. They don't allow it any other way.

There are setup instructions inside you gmailbox, and you may have to enable pop/smtp for your account.

---

### Post by t0p on 2009-07-10
> **t4thfavor said:**
> smtp.gmail.com:587, using tls encryption. They don't allow it any other way.


Thanks.  That was it.  But now I get the following error:

```
Jul 10 10:56:52 machine sendEmail[19699]: ERROR => No TLS support!  SendEmail can't load required libraries. (try installing Net::SSLeay and IO::Socket::SSL)

```

I don't know where to get those files (libraries?)  **sudo apt-get install Net::SSLeay** doesn't do any good.  Can anyone help?

---

### Post by t0p on 2009-07-10
Oh my.  I found Net::SSLeay [here]("http://search.cpan.org/~flora/Net-SSLeay/lib/Net/SSLeay.pm").  I downloaded and tried to build it, but got an error when running **sudo make install**.  The error was like this:

```
SSLeay.c:959: error: declaration for parameter ‘XS_Net__SSLeay_CTX_flush_sessions’ but no such parameter
SSLeay.c:935: error: declaration for parameter ‘XS_Net__SSLeay_CTX_remove_session’ but no such parameter
SSLeay.c:911: error: declaration for parameter ‘XS_Net__SSLeay_CTX_add_session’ but no such parameter
SSLeay.c:891: error: declaration for parameter ‘XS_Net__SSLeay_CTX_free’ but no such parameter
SSLeay.c:868: error: declaration for parameter ‘XS_Net__SSLeay_CTX_new_with_method’ but no such parameter
SSLeay.c:845: error: declaration for parameter ‘XS_Net__SSLeay_CTX_tlsv1_new’ but no such parameter
SSLeay.c:822: error: declaration for parameter ‘XS_Net__SSLeay_CTX_v23_new’ but no such parameter
SSLeay.c:799: error: declaration for parameter ‘XS_Net__SSLeay_CTX_v3_new’ but no such parameter
SSLeay.c:776: error: declaration for parameter ‘XS_Net__SSLeay_CTX_v2_new’ but no such parameter
SSLeay.c:753: error: declaration for parameter ‘XS_Net__SSLeay_CTX_new’ but no such parameter
SSLeay.c:728: error: declaration for parameter ‘XS_Net__SSLeay_hello’ but no such parameter
SSLeay.c:705: error: declaration for parameter ‘XS_Net__SSLeay_constant’ but no such parameter
SSLeay.xs:354: error: declaration for parameter ‘ssleay_ctx_cert_verify_cbs’ but no such parameter
SSLeay.xs:204: error: declaration for parameter ‘ssleay_RSA_generate_key_cb_t’ but no such parameter
SSLeay.xs:203: error: declaration for parameter ‘ssleay_session_secret_cb_t’ but no such parameter
SSLeay.xs:202: error: declaration for parameter ‘ssleay_ctx_cert_verify_cb_t’ but no such parameter
SSLeay.xs:201: error: declaration for parameter ‘ssleay_ctx_passwd_cb_t’ but no such parameter
SSLeay.xs:195: error: declaration for parameter ‘ssleay_ctx_passwd_cbs’ but no such parameter
SSLeay.xs:132: error: declaration for parameter ‘ssleay_ctx_verify_callbacks’ but no such parameter
SSLeay.xs:128: error: declaration for parameter ‘perl_filehandle_t’ but no such parameter
SSLeay.c:8547: error: expected ‘{’ at end of input
make: *** [SSLeay.o] Error 1

```

but it goes on in a similar vein - I can't scroll back the terminal far enough to get it all.

In the module's notes, it warns I might need to recompile perl and openssh to work successfully with Net::SSLeay - apparently they need to be compiled with the same compiler.

That is an awful lot for little me to do.  So: before I embark on a mad recompiling adventure from which I may never return, **does anyone know of a command-line email utility I can use in a script and which supports sending through an smtp server like google's?**  I looked at **mailx** but the manpage is so long... there are so many options...

---

### Post by t4thfavor on 2009-07-10
Well at least we got you this far. Try sending the mail directly without using the gmail relay, My untangle server sends mail to gmail all day long using himself as the relay. You may get smacked by spam blockers, I'm just saying that I don't and I send about 7 emails a day to my gmail via sendmail.

---

### Post by t0p on 2009-07-10
> **t4thfavor said:**
> Well at least we got you this far. Try sending the mail directly without using the gmail relay, My untangle server sends mail to gmail all day long using himself as the relay. You may get smacked by spam blockers, I'm just saying that I don't and I send about 7 emails a day to my gmail via sendmail.

Well, when I have tried to send email using the **mail** command, the program sends me a mail (through my computer's mail system to my /var/mail box, not through any outside agency) saying that sending to remote domains is not supported.  I've been looking at the manpage for **exim4**, but I've never found manpages to be very clear and I'm having great difficulty getting a handle on the program's syntax.  Maybe someone could explain how I can use **exim4** or **sendmail** from the command line?  The manpage for exim4 says that in one mode I need to write everything to STDIN, including headers.  Is this truly as simple as a command line client can get???

**EDIT:** *sigh* Using exim is the same as mail - I get a mail delivery failed message saying that sending to remote domains is not supported.  So it looks like I need a program that will send mail via my gmail smtp server.  Is there a way to run evolution from a script?  Can any command line MTA like mutt for example use gmail's smtp server?  It's going to take me ages to trawl through all the possibilities.  If someone here knows the answer, please clue me in.

---

### Post by t0p on 2009-07-11
Okey-dokey... I couldn't get anywhere with sendEmail.  So I gave the problem some thought and research - and EUREKA! - success!!

I reconfigured exim4, as described on [wiki.debian.org]("http://wiki.debian.org/GmailAndExim4").  So now I can compose and send email from the command line, via smtp.gmail.com, to the intended recipients.  Success!!

---

### Post by andrew.46 on 2009-07-11
Hi t0p,

> **t0p said:**
> can someone suggest a command-line mail program I can use in a script that *will* work with a gmail smtp server?

Although I see you have already achieved success there is another approach. You could use some pieces of the following guide:

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

This guide does not deal with the direct commandline usage of mutt but this should be easy enough to put together after following the basic guide.

Andrew

---

### Post by luigi_mb on 2009-07-12
> **t0p said:**
> Thanks.  That was it.  But now I get the following error:

```
Jul 10 10:56:52 machine sendEmail[19699]: ERROR => No TLS support!  SendEmail can't load required libraries. (try installing Net::SSLeay and IO::Socket::SSL)

```

I don't know where to get those files (libraries?)  **sudo apt-get install Net::SSLeay** doesn't do any good.  Can anyone help?

Using Synaptic, get libnet-ssleay-perl and libio-socket-ssl-perl .

/luigi

---

### Post by dopple on 2009-07-24
Also, just to save anyone wanting to break their keyboard... the username (-xu) should be WITHOUT the @gmail.com suffix. ](*,)

---

