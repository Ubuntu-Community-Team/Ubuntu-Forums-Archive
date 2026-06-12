---
title: "Using ssh/ssl rsa keys to secure services"
date: 2009-08-22
forum: General Help
---

### Post by terrigat on 2009-08-22
These commands seem accurate for producing the files for what is needed in a x11vnc/ssvnc connection that verifies the client & server to each other using certificates.
You will need to choose where you want the files to be created.

This is completely unnecessary if you want to build this strictly for x11vnc/ssvnc. This is an example of using the base commands to generate what is needed to secure this service using openssl. If you just want to use this for x11vnc/ssvnc follow krunge's steps below.

# Generate a new rootCA certificate
# This can make issuing / revoking certificates much easier depending on how
# large your userbase is
openssl req -new -x509
# -x509 is used for self-signed certificates
-config ./openssl.cnf \
# any custom changes to the default /usr/lib/ssl/openssl.cnf
-extensions v3_ca -days 3650 \
# 3650 means certificate is valid for roughly 10 years
-newkey rsa:2048 -keyout ./private/myCA.key \
# rootCA private key
-out ./certs/myCA.crt
# rootCA selfsigned certificate

# Generate a new certificate signing request for a server certificate
openssl req
-config ./openssl.cnf \
-days 3650 \
-newkey rsa:2048 -keyout ./private/vnc_pem.key \
# private key
-out ./csr/vnc_pem.csr
# signing request file

# Sign the request with the myCA key:
openssl ca
-config ./openssl.cnf \
-days 3650 -notext -policy policy_anything \
-keyfile ./private/myCA.key \
# myCA private key
-cert ./certs/myCA.crt \
# myCA certificate
-in ./csr/vnc_pem.csr \
# signing request
-out ./certs/vnc_pem.crt
# signed certificate

You can follow the same steps for creating another for the ssvnc client


vnc_pem.key has:
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----

vnc_pem.crt has:
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----

without -notext under openssl ca you get this:

certificate
...
modulus
...
signature algorithm
...
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----

which stunnel can't read properly

Not sure if -policy policy_anything is required but almost every helper program uses it so.

ssl [pem] actually requires:
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----
so
cat vnc_pem.key vnc_pem.crt >> vnc-server_key-crt.pem
Do the same with the ssvnc clients files.
NOTE: you can use -ssl SAVE-filename and have server-filename.[pem|crt] in -ssldir [path] if you want. I did not fully test it though.
-sslverify CA requires alot of files & folders to be in exact places with exact filenames so use at your peril unless following krunge's steps below which creates everything using x11vnc.

x11vnc -nopw -forever -bg -o /var/log/x11vnc.log \
-ssl ./vnc-server_key-crt.pem \
-sslverify ./certs/myCA.crt \
-display :0

Do notice how because sslverify is using the rootCA.crt to verify that the server doesn't need the clients keys or certs.

If you want this run run at startup, add it to /etc/gdm/Init/Default on the server.
and change:
/etc/gdm/gdm.config-custom
to include
KillInitClients=false
under the header
[daemon]

ssvnc on the client will need vnc-client_key-crt.pem & the myCA.crt
.pem is mycert & myCA.crt is for server cert

hostname:n & you should be good

***WARNING***
work-in-progress
this lets you access without a password to display 0. The good news is that if the server or client is missing the CA signed certificates, that computer cannot connect.

---

### Post by terrigat on 2009-08-29
Since my last question was ignored, I will assume that my attempt was hard to follow.
I've changed the above to show an example of something I'm trying to accomplish using openssl.

---

### Post by krunge on 2009-08-29
I've looked at your steps briefly (but not in detail) and they look OK, although I am confused about a few things.

One thing I am not sure about is if the x11vnc -ssl SAVE-... will pick up your server key.  To be sure, why not just use the full path instead:
```
-ssl /etc/ssl/private/vnc_pem.key
``` and with no "-ssldir" needed.

Hmmm now that I think about it this file may need **both** key and crt inside it... see the x11vnc steps I mention below and look at the generated file "server-myvnc.pem".

From your rootCA you are generating and signing a **single** key+cert pair that it seems you want to use for authenticating **BOTH** the vnc server and vnc client.  Is this correct and what you want or have I missed something? You also haven't mentioned steps copying any cert/key to the VNC Viewer side and using it.

Anyway, x11vnc can do all of these openssl(1) commands for you. Let me show you how and you can either use that or try to figure out what the differences are with your manual steps.

I will use "/tmp/ssl/private" instead of "/etc/ssl/private" to keep things cleanly separated for me, you can change  to /etc or whereever you want.

```
# Create x11vnc's Certificate Authority (CA) key+cert:

x11vnc -env REQ_ARGS='-days 3650' -sslGenCA -ssldir /tmp/ssl/private

# (follow the prompts, supply passphrase, etc.)  This creates:
# /tmp/ssl/private/CA/*  including cacert.pem and private/cakey.pem


# If you want 3650 days for the client and server keys signed by CA the
# REQ_ARGS trick doesn't work and you will have to manually edit 
# /tmp/ssl/private/CA/ssl.cnf* and change it from 730 to 3650.


# Create a signed key for the VNC Viewer side 'unknown':

x11vnc -sslGenCert client unknown -ssldir /tmp/ssl/private

# (follow the prompts.  For testing, do not protect this key with passphrase.)
# This creates: /tmp/ssl/private/clients/unknown.{crt,pem}


# Create a (different) signed key for the x11vnc VNC Server side 'myvnc':

x11vnc -sslGenCert server myvnc -ssldir /tmp/ssl/private

# (follow the prompts.  For testing, do not protect this key with passphrase.)
# This creates: /tmp/ssl/private/server-myvnc.{crt,pem}


# Copy the Vnc Viewer's key+crt file to the client machine, e.g.

scp -p /tmp/ssl/private/clients/unknown.pem username@client-machine:.

# (or whatever means you need to copy files to Windows, etc.)


# Start up x11vnc to test:

x11vnc -ssldir /tmp/ssl/private -ssl SAVE-myvnc -sslverify CA -display :0

# (thus x11vnc presents himself using 'myvnc' and verifies incoming
# VNC clients against the CA cert: only ones signed by it are allowed in.)


# Run SSVNC on Windows (or MacOSX or Linux ...):
#
# Click on 'Certs'.  Set 'MyCert' to the 'unknown.pem' file you copied.
# UN-select 'Verify All Certs' (for the first test at least.)
# Put hostname:0 in 'VNC Host:Display' where hostname is where x11vnc is
# running and we assume x11vnc got port 5900 (use hostname:N otherwise.)
# Then click on 'Connect'.  It should work...


# This way, that avoids -ssldir and use full pathnames, should work too:

x11vnc -ssl /tmp/ssl/private/server-myvnc.pem -sslverify /tmp/ssl/private/CA/cacert.pem -display :0

```

To have the VNC Viewer (SSVNC) authenticate x11vnc against the CA cert do these extra steps:
```
# Copy the CA Cert file to the client machine, e.g.

scp -p /tmp/ssl/private/CA/cacert.pem username@client-machine:.

# (or whatever means you need to copy files to Windows, etc.) 


# Start up x11vnc as before.

# SSVNC on Windows (or MacOSX or Linux ...):
#
# In addition to the other steps, also do:
#
# Click on 'Certs'.  Set 'ServerCert' to the 'cacert.pem' file you copied.
#
# Connect as before.  If there are problems, look at the STUNNEL.EXE log file.

```
Well this is a long post with lots of instructions.  I'll let you reply with questions and/or problems.  I will make a new post replying to some of your other questions.

---

### Post by krunge on 2009-08-29
> **terrigat said:**
> The idea is ssvnc on windows (yeah, windows) connects using 'unknown' to server using vnc to access the gdm(?) user / password login screen & if user has a saved (not logged out) session, they have the choice to resume saved session (desktop) but forces login again to access.
The x11vnc option [-xdmsvc]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-xdmsvc") might be useful for this.  More help later if you go that path.
> 
If this works, I'll add it to /etc/gdm/Init/Default on the server.
I know this doesn't solve the required login but I don't think x11vnc is the way to handle it.
Well, the -xdmsvc option above (that uses the x11vnc [-unixpw]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-unixpw") mechanism) might be good enough.
> Does the Common Name have to be correct at the time of testing for this to work?
Does the Common Name of the certificate have to match the location / IP of the client or can I use the same one for all clients that want to connect?
or to put it another way: can all the info in the certificate just be the servers info?
 No, they can be different.  The only time I've seen this matter is if you are using x11vnc's SSL Java applet.  Then your Web Browser and/or Java VM will supply extra prompts about the mismatch and if you want to continue. In that case it would pay to make them match.  ssvnc/stunnel do not check for this AFAIK.
> ...
is this correct or do they need to be in one file together?
 See my earlier post.  I believe the file referred to by the "-ssl" option must contain both the key and the cert.
> 
what good is the newcerts/randomname.pem file thats identical to vnc_pem.crt
Made by one of your manual openssl(1) commands?  I'm not sure.  Must be part of openssl procedure/config.  Maybe to revoke later?

---

### Post by terrigat on 2009-08-30
I did see the -sslGenCert / -sslGenCA args & also know about CA.pl plus a few other helper programs. This is just an example of something I am attempting with openssl, so I am trying to get use to the basic openssl req/gen/ca commands. Most of the examples (and I do mean most) show broken examples that don't actually work or they use improper methods which kinda work. My favorite was the missing 'ca.txt' file referred to on the openssl website 'certificates.txt.'

The man pages make it sound like it will overwrite the file everytime if I don't use the 'SAVE-[]' directive.

Also according to ssvnc the two files needed are:
vnc_key-crt.pem for the client (private key & certificate)
and
vnc_pem.crt for the server (certificate)

Makes it look like the server has no need for the private key (which kinda makes sense) so:
x11vnc -ssl -sslverify /etc/ssl/certs/vnc_pem.crt ...
or the server still needs a private key:
x11vnc -ssl SAVE-/etc/ssl/private/vnc_pem.key -sslverify /etc/ssl/certs/vnc_pem.crt ...

If I use the -display:0 switch will multiple users be able to connect at the same time?
I had not looked at -xdmsvc just yet, didn't want to get ahead of myself. The basic idea is for the users to have an icon that they use to open a gui login on the server. If I was the only one using this, I would just use ssh tunnels on localhost like I have for years. The man makes it sound like a terminal login window which doesn't quite suite my users.

As far as getting the files onto different computers I am keeping that open but I do have many good secure ways to get them to the required computers (although they are windows systems so...)

Sorry to say I cant do testing until much later tonight.

---

### Post by krunge on 2009-08-30
> ...
My favorite was the missing 'ca.txt' file referred to on the openssl website 'certificates.txt.'
Yes, this is difficult to get working (at least I found it was); that is why x11vnc tries to insulate the user from that with the automatic running of openssl(1) for these certificate creation activities.

Of course a power-user like you who knows how to create them himself can always use "-ssl /full/path/to/file.pem" and/or "-sslverify /full/path/to/ca.pem".   
> 
The man pages make it sound like it will overwrite the file everytime if I don't use the 'SAVE-[]' directive.

Which part?  In the x11vnc 0.9.9 documentation or the older one on ubuntu? Since then it has changed that "-ssl" implies "-ssl SAVE".  Previously "-ssl" implied "-ssl TMP" (temporary session key+cert created each time.) Does the man page really sound like it will overwrite your "-ssl /full/path/to/file.pem"?
> 
Also according to ssvnc the two files needed are:
vnc_key-crt.pem for the client (private key & certificate)
and
vnc_pem.crt for the server (certificate)

I'm not sure what you mean by "needed".  *If* the ssvnc user wants to authenticate the vnc server, then the vnc server's cert will be needed (or verified manually at the first connection.)  *If* the ssvnc user is required to authenticate himself to x11vnc via SSL, then a user key+cert is needed. 

Both of these are optional in general, but for your usage it sounds like you want both.

BTW, in my previous post I showed an example how to handle the server cert part: you just use the 'cacert.pem' I mentioned.
> 
Makes it look like the server has no need for the private key (which kinda makes sense) so:
x11vnc -ssl -sslverify /etc/ssl/certs/vnc_pem.crt ...
or the server still needs a private key:
x11vnc -ssl SAVE-/etc/ssl/private/vnc_pem.key -sslverify /etc/ssl/certs/vnc_pem.crt ...

Well for the SSL protocol, the server side *must* present a certificate. So for the "-ssl" all by itself x11vnc will create a server cert automatically via openssl(1). (in recent x11vnc's "-ssl" implies "-ssl SAVE" so the created one will be saved for future use.)

For the client SSL authentication is optional and only rarely done (but, of course, you are forcing the client to provide a cert by using -sslverify.)  Usually client authentication is done externally (outside of SSL) via password, etc, once the encrypted channel is set up.
> 
If I use the -display:0 switch will multiple users be able to connect at the same time?
Oh, I just meant '-display :0' to get started testing.  I think you should get the SSL working OK before you address the multi-user access you are considering.
> 
The man makes it sound like a terminal login window which doesn't quite suite my users.
 Not sure what you mean.  For -xdmsvc/-unixpw?  It is not too bad, have you tried it?
> 
As far as getting the files onto different computers I am keeping that open but I do have many good secure ways to get them to the required computers (although they are windows systems so...)

For this to be secure (no man-in-the-middle possibility) you must copy/transfer SSL certificates by some means. This must be done before the actual SSL connection takes place.  Or you could pay Verisign or Thawte to sign them then you could use Verisign/Thawte certificates that are already on basically all machines.

BTW, note that SSVNC can be used to create the user's key+cert.  Then only certificates (i.e. public key part) need to be transferred.  If certificates are sniffed by a bad person during transfer that is no big deal (however if the bad person can modify them in transfer then all bets are off.)
> 
Sorry to say I cant do testing until much later tonight.
Report back here to me how it goes.  Get the SSL working to your satisfaction and then we can address the 'user login / gdm' aspect.

---

### Post by terrigat on 2009-08-31
I've been using this website for my information:
[http://www.karlrunge.com/x11vnc](http://www.karlrunge.com/x11vnc)
That is why I assumed it was done -ssl TMP still if -ssl SAVE- wasn't specified. Sorry 'bout that.

I'm not sure what you mean by "needed"...
Was needed too strong a word? I did not want another password system (yes I know its the same user/password files) to throw at my users. I was hoping to only show them one user/password screen while keeping out random attempts in the meantime. Since my users will connect using a preconfigured vnc-client, I was more worried about blocking unwanted login attempts on the server than if they are connecting to the wrong system. If the first defense for the server login is "does the user have the key/crt/??" then my worries shift over to social engineering & outright theft. Outside of running a full authentication server, this seemed a reasonable solution. Right now I've got 7 users, 3 laptops, 4 desktops, 3 servers & 2 routers.

As stupid as this may sound, your last post was the first time I've had a concrete answer as to the certificate being the public key. Yes, I know that its quite logical to assume, but since I never came across an absolute answer before its a relief to see it posted. Probably the main reason I can't think of what info to use in the certificate creation is b/c I don't know what it will be used for.

My original question was more to understand what I was getting out of these commands & if I was using the result correctly. The vnc connection bothered me the most due to the danger of a direct connection to the desktop protected by passwords. If it was a single password of my choice then no real problem, but its multiple passwords that I don't have control over. If I was to ask for clarification from an expert on anything, this was it. It's not that I didn't try ahead of time. Its that the literature is obtuse. Here I am, 2 books & 20+ articles later and I'm still asking basic questions. Is it obvious enough that this is my first real foray into 'why' as opposed to 'how?'

Whew, that was longer than intended!

---

### Post by krunge on 2009-08-31
I like your plan to use VNC viewer-side SSL key+cert's to severely limit which machines can even connect in the first place.  That is a nice first layer of security.

The example in my first post  showed how to do this; the SSL key+cert creation, copying, and use of x11vnc -sslverify.  If you have any questions about this mechanism please ask.

I am confused about your next layer or security.  In particular, do the remote users each have their own Unix account?   (I.e. they use their own account, for which they know the unix password, in the GDM login screen.) Or will they somehow share a single Unix account?

If the latter, I am not sure what procedure you are intending they use to avoid interfering with each other.  Could you say more?

If the former, I would claim x11vnc's '-svc' mode gives you basically all that you want.  If you feel they must see the GDM (XDM, etc) login greeter screen then you can use '-xdmsvc' (but note that when they connect the first time they will need to enter their unix password twice.)

BTW, I assume you want "virtual X sessions" instead of ones running on the physical display hardware, right?  I.e. one server with multiple user sessions at the same time, that exist virtually in RAM only.  The x11vnc -svc and -xdmsvc modes will give you these virtual X sessions.

---

### Post by krunge on 2009-08-31
> If the former, I would claim x11vnc's '-svc' mode gives you basically all that you want.Before I forget, let me give complete examples for the '-svc' and '-xdmsvc' cases.

In a earlier post I showed how to create CA (cacert), server (myvnc), and client (unknown) key+cert pairs in /tmp/ssl/private and to copy the 'unknown.pem' and 'cacert.pem' to the VNC Viewer side (where SSVNC will be used as the viewer.)  I assume that this has been done. Just follow the steps in post #3.

Let's use inetd to provide the service; add this line to /etc/inetd.conf:
```

5900  stream  tcp  nowait  root  /usr/sbin/tcpd /usr/bin/x11vnc -inetd -svc -ssldir /tmp/ssl/private -ssl SAVE-myvnc -sslverify CA -o /var/tmp/x11vnc.log

```Then restart inetd (e.g. /etc/init.d/openbsd-inetd stop then start). It should be easy to adapt the above to xinetd.

For debugging, the x11vnc output is collected in /var/tmp/x11vnc.log. Examine it if there are problems connecting.

Then the user at the SSVNC VNC Viewer (on Windows, Unix, or MacOSX) sets 'MyCert' to the copied 'unknown.pem' file and 'ServerCert' to the copied 'cacert.pem' file.  Next, the user puts in 'hostname:0' in the VNC Display entry box ('hostname' should be the actual hostname or IP address of the machine running inetd/x11vnc.)

Then the user clicks on 'Connect'.  Once connected, he will be asked to supply his unix username and password.  An Xvfb X server running his session will be created if there is not one running for him yet.  Otherwise it simply attaches to his existing Xvfb.

The user can disconnect and reconnect to this X session via VNC as many times as he likes.  When he wants to terminate the X session he 'logs out' of it the regular way and Xvfb exits.

At the SSVNC viewer, the user can save these settings (the cert filenames and hostname) as a 'profile' to be easily loaded and reconnected to later. For your users, you could create the profile as part of the distributed package.

> 
If you feel they must see the GDM (XDM, etc) login greeter screen then you can use '-xdmsvc' (but note that when they connect the first time they will need to enter their unix password twice.)
To use a GDM/XDM/KDM/etc greeter in this scheme, change '-svc' to '-xdmsvc' in the inetd line and add something like:
```

[xdmcp]
Enable=true

```to /etc/gdm/gdm.conf or whereever the config file is or whatever the  analogous changes are for your display manager if it is not gdm. Then restart GDM/etc.

An advantage to using GDM/etc is that the user has a point and click interface to select his type of session, etc.

So now when the user connects in the same way as above and supplies his unix username and password he gets the GDM (or whatever your display manager is) greeter panel.  So he would have to supply his username and password (yet again) to the greeter.  Once he has a session, when he reconnects via VNC he will be automatically connected to his session (no GDM greeter panel until he logs out of that X session.)

---

### Post by krunge on 2009-09-02
BTW, one more thing I wanted to mention to you, since you seem to be relatively new to these things, is some other software to consider.  Although I, personally, do not care for it because it is 1/2 closed source and a competitor, you may want to look into nomachine.  Since it is based on a commercial product you may find it easier to setup and use. There can be trouble configuring it, but I think if you stick with the packages from their site things should go smoothly.

---

### Post by terrigat on 2009-09-02
Sorry about the delay.  Lots of testing to figure out what x11vnc needs. Turns out that it will only look at certain filenames in certain places.  After working out the exact paths that x11vnc needs plus the file types/names it requires, I've gotten it to load the key/crt/pem files + made sure that there would be no CN/DN collisions just in case.

x11vnc -nopw -o /var/log/x11vnc.log -ssl /etc/ssl/x11vnc/certs/vnc-server_key-crt.pem -sslverify /etc/ssl/x11vnc/clients/vnc-client.crt -display :0

ssvnc has vnc-client_key-crt.pem & vnc-server.crt

I didn't use -bg because then I would see in the terminal window if the service failed to load.

I get "ReadExact: Socket error while reading" from ssvnc on the XP system while the /var/log/x11vnc.log shows that the serverside loaded successfully.

It happens right after passphrase requested prompt. It doesn't wait for the password before giving the error.

stunnel gives SSL3_GET_RECORD:wrong version number which makes it sound like one of the two services isn't using SSL v3. Ssvnc doesn't have an option to try different ssl versions & x11vnc shouldn't be using an older version right?


using serverside:
x11vnc -display :0

ssvnc works with "//vnc:ip-address:0"
&
ultravnc works as well


You certainly put alot together for me. I am grateful although had hoped to not waste too much of your (or the communities) time. Thank you!!

---

### Post by krunge on 2009-09-02
> **terrigat said:**
> 
I get "ReadExact: Socket error while reading" from ssvnc on the XP system while the /var/log/x11vnc.log shows that the serverside loaded successfully.

The easiest way for me to troubleshoot this will be for you to attach to a post the full, complete x11vnc output file and the full, complete STUNNEL.EXE log.  I suggest using the file-attach feature of the Reply composer, or you could send them to me via Private message if you wanted to.

I don't suggest directly pasting them into your reply since the files are so long and will dilute this thread's potential value.

Cheers.

---

### Post by terrigat on 2009-09-03
x11vnc.log file removed

---

### Post by terrigat on 2009-09-03
stunnel.txt file removed

---

### Post by krunge on 2009-09-03
> **terrigat said:**
> here is the x11vnc.log file with .txt extension
nothing really here; mostly just comments.I looked at the x11vnc.txt logfile.  No VNC viewer ever connected to that x11vnc.

x11vnc will log each connection attempt with some information.  I see nothing, so you never even contacted x11vnc.

I see something useful in the logfile:```
03/09/2009 01:24:51 Autoprobing TCP port
03/09/2009 01:24:51 Autoprobing selected port 5901
03/09/2009 01:24:51 openssl_port: listen on port/sock 5901/9

The SSL VNC desktop is:  server:1
```So did you point SSVNC to 'server:1'?  Or perhaps use an IP nn.nn.nn.nn:1 if the name 'server' does not resolve.

You probably have some other VNC Server running on the default VNC port 5900 (i.e. server:0  ) Check for other VNC servers you started.  It could even be another x11vnc you started in the background that is still running (evidently without SSL.)

---

### Post by terrigat on 2009-09-03
I uploaded better logs. I think I rushed the setup last time. I couldn't find a netstat entry for vnc so I'm not sure what had taken port 5900.

I do remember this getting past the verify setup before but I can't seem to recreate it. The reason the ssvnc service has the vnc-server.crt is BECAUSE the server transmitted it to ssvnc. I had forgotten to move it over manually beforehand.
These computers are on the same switch using 192.168.72.19x as their addresses (4=XP/3=ubuntu) & I disabled the XP PC's firewall(s).  I'm glad I did not move the server to its headless location already.  That terminal is no fun to use.

---

### Post by krunge on 2009-09-03
> **terrigat said:**
> I uploaded better logs. I think I rushed the setup last time. I couldn't find a netstat entry for vnc so I'm not sure what had taken port 5900.Yes, those are better logs, at the bottom of x11vnc.txt you can see your connection attempts.

From the STUNNEL log on Windows:
```

2009.09.03 09:52:05 LOG4[3544:3596]: VERIFY ERROR: depth=0, error=unable to get local issuer certificate: /C=US/ST=Maryland/O=Infradad/CN=gwin.vnc-server
2009.09.03 09:52:05 LOG3[3544:3596]: SSL_connect: 14090086: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
2009.09.03 09:52:05 LOG5[3544:3596]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket

```So you have messed up the certs somehow and your SSVNC/STUNNEL is not allowing the x11vnc.  My guess you are not using the CA certificate in the SSVNC Certs -> ServerCert setting, but rather using some other certificate.

What happens when you follow the example I gave in Post #3 to the letter?

---

### Post by terrigat on 2009-09-03
new log files take two.  Got rid of the failed message. But right afterwards it starts the old problem again.

I've followed your instructions & it worked of course.  I seems that a few things are different about the structure of the signed certificates.

**The certificates produced by the working commands didn't have the:**
certificate
...
modulus
...
signature algorithm
...

**part. just this:**

-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----

**could this have made a difference?**

---

### Post by terrigat on 2009-09-04
**Will this produce the needed files in the appropriate style? maybe I can't use these as Common Names?**

**CN: gwinCA**
openssl req -new -x509 -config /etc/ssl/openssl.cnf \
-newkey rsa:2048 -keyout /etc/ssl/private/gwinCA.key \
-out /etc/ssl/certs/gwinCA.crt

**CN: gwin.vnc-server**
openssl req -config /etc/ssl/openssl.cnf \
-newkey rsa:2048 -keyout /etc/ssl/private/vnc-server_pem.key \
-out /etc/ssl/csr/vnc-server_pem.csr

openssl ca -config /etc/ssl/openssl.cnf -extensions v3_ca \
-keyfile /etc/ssl/private/gwinCA.key \
-cert /etc/ssl/certs/gwinCA.crt \
-in /etc/ssl/csr/vnc-server_pem.csr \
-out /etc/ssl/certs/vnc-server_pem.crt

**CN: gwin.vnc-client**
openssl req -config /etc/ssl/openssl.cnf \
-newkey rsa:2048 -keyout /etc/ssl/private/vnc-client_pem.key \
-out /etc/ssl/csr/vnc-client_pem.csr

openssl ca -config /etc/ssl/openssl.cnf -extensions v3_ca\
-keyfile /etc/ssl/private/gwinCA.key \
-cert /etc/ssl/certs/gwinCA.crt \
-in /etc/ssl/csr/vnc-client_pem.csr \
-out /etc/ssl/certs/vnc-client_pem.crt

cat ./private/vnc-client.key ./certs/vnc-client.crt >> vnc-client_key-crt.pem
**#file used in ssvnc**
cat ./private/vnc-server.key ./certs/vnc-server.crt >> vnc-server_key-crt.pem [B]#file used for server

[/B]** then I moved the files into a separate directory structure so I wouldn't ruin everything else (/etc/ssl/x11vnc) so:**
x11vnc -nopw -forever \
-ssl /etc/ssl/x11vnc/certs/vnc-server_key-crt.pem \
-sslverify /etc/ssl/x11vnc/clients/vnc-client.crt

**These are the steps I attempted that produced the errors. Did I break something in the process?**
**Maybe:**
x11vnc -nopw -forever \
-ssl /etc/ssl/x11vnc/certs/vnc-server_key-crt.pem \
-sslverify /etc/ssl/x11vnc/CA/gwinCA.crt

---

### Post by krunge on 2009-09-04
> **terrigat said:**
> I've followed your instructions & it worked of course.
Good, glad my example works for you.
> 
I seems that a few things are different about the structure of the signed certificates.

**The certificates produced by the working commands didn't have the:**
certificate
...
modulus
...
signature algorithm
...

**part. just this:**

-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----

**could this have made a difference?**
Possibly.  To be honest I've never seen anything besides  the 'BEGIN CERTIFICATE' format so I don't really know what to say about the other format you are generating...

---

### Post by krunge on 2009-09-04
> **terrigat said:**
> **Will this produce the needed files in the appropriate style? maybe I can't use these as Common Names?**

The choice of common names won't matter at all.  SSVNC/STUNNEL ignores the actual choice (x11vnc ignores them too.)

By "ignore" I guess I mean it doesn't do a computer hostname check like web browsers do.  Of course the certificate on one side must correspond to the key+cert on the other side.
> 
**CN: gwinCA**
openssl req -new -x509 -config /etc/ssl/openssl.cnf \
-newkey rsa:2048 -keyout /etc/ssl/private/gwinCA.key \
-out /etc/ssl/certs/gwinCA.crt

...

Well I don't have the time to debug your experiments with the openssl(1) command.  But I will provide you with the raw openssl commands x11vnc runs (I pulled these out of the x11vnc sourcecode):
```

genCA openssl call:

   Generate the CA req call:

      "$OPENSSL" req -config "$DIR/CA/ssl.cnf" -new -x509 -days 730 $req_args  \
              -keyout "$DIR/CA/private/cakey.pem" \
              -out "$DIR/CA/cacert.pem"

genCert openssl calls:

   self-signed req call:

      "$OPENSSL" req -config "$cnf" -nodes -new -newkey rsa:2048 -x509 $req_args \
              -keyout "$DIR/$dest.key" \
              -out    "$DIR/$dest.crt"

   CA-signed req call:

      "$OPENSSL" req -config "$cnf" -nodes -new -newkey rsa:2048 $req_args \
              -keyout "$DIR/$dest.key" \
              -out    "$DIR/$dest.req"

   Encrypt a key:

      "$OPENSSL" rsa -in "$target" -des3 -out "$target"


   CA-signed ca call:

      "$OPENSSL" ca -config "$cnf" -policy policy_anything -notext \
              -in  "$DIR/$dest.req" \
              -out "$DIR/$dest.crt"


```
Sorry for the cryptic code dump from x11vnc, as I said I don't have the time to    check everything you have done.

I am hoping you can compare the above openssl commands to what you have done and notice the important difference that makes your manual method fail.

Good luck.

---

### Post by terrigat on 2009-09-04
Okay, I found some answers which may help.

openssl ca is generating a format that is NOT usable. This is the reason I found no documentation on the subject & why CA.pl or sign.sh is used in its place.

According to openssl.org  the ca command is not recommended due to unpredictable results.

I guess I'll need to modify sign.sh to produce what I want instead of trying to use openssl ca.

unless...

I think this is the relevant commands that I was missing:
-policy policy_anything -notext

---

### Post by krunge on 2009-09-04
> **krunge said:**
> But I will provide you with the raw openssl commands x11vnc runs (I pulled these out of the x11vnc sourcecode):
...

A couple notes that will possibly help you with your troubleshooting.

1) You will need to look at the x11vnc 'ssl.cnf', etc, openssl config files that are passed in via the '-config ...' to openssl(1) to get the full story.

2) As I believe you have mentioned, note that x11vnc will combine '.key' and '.crt' (private SSL key and public SSL certificate) contents into a single '.pem' file:
```

genCert call:

        cat  "$DIR/$dest.key"  "$DIR/$dest.crt" \
                > "$DIR/$dest.pem" || exit 1

``` 
I believe this is a standard practice.  At least stunnel uses it and I also see a file /etc/ssl/certs/imapd.pem like this on my system.

---

### Post by krunge on 2009-09-04
> **terrigat said:**
> 
openssl ca is generating a format that is NOT usable. This is the reason I found no documentation on the subject & why CA.pl or sign.sh is used in its place.

According to openssl.org  the ca command is not recommended due to unpredictable results.

I'm not sure what you mean.  CA.pl is just a perl script wrapper to 'openssl ca ...' (and other openssl cmds) right?

x11vnc's wrapper scripts also call 'openssl ca ...' (shown in my earlier post.)

The man page ca(1) seems to document it pretty well.
> 
I think this is the relevant commands that I was missing:
-policy policy_anything -notext
Note that "policy_anything" is defined in the x11vnc's ssl.cnf (and related) file that gets passed to openssl(1) via the -config option.

---

### Post by terrigat on 2009-09-04
Those two options for openssl ca [-policy policy_anything -notext] solved it.  My certificates now work as expected.

I wish I had known to look there so that I could've saved US the headache.

---

### Post by krunge on 2009-09-04
> **terrigat said:**
> Those two options for openssl ca [-policy policy_anything -notext] solved it.  My certificates now work as expected.

Good glad it is working for you now.

Can you tell if it was the 'policy_anything' or '-notext' that did the trick?

I see now that 'policy_anything' is a part of the basic openssl.cnf (i.e. x11vnc didn't change it.)  If you look inside CA.pl you will see it referring to policy_anything for many of its actions.

---

### Post by terrigat on 2009-09-04
I updated the 1st post with working commands & hopefully helpful notes. Probably still too rough.

---

