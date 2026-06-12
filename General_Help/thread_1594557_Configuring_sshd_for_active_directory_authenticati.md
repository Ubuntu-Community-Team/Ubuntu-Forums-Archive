---
title: "Configuring sshd for active directory authentication"
date: 2010-10-12
forum: General Help
---

### Post by GMX750 on 2010-10-12
Hi all. I've spent the last week googling for sollutions to my problem like crazy.. I decided that the best approach would be to register in a forum and explain my goal.

I have installed Turnkey Linux's Trac appliance. I have successfully setup my apache with active directory authentication.. and I was trying to do the same for my subversion repositories... although I have been able to do it for HTTP/HTTPS access via apache configuration... what I need is to have a user and password prompt when I use TortoiseSVN to acces my subversion repository using "svn+ssh". As I have read in SVN documentation, SSH handles the authentication requests, therefore I think I will have to do something regarding my ssh configuration files..(?)
currently I access my repository via TortoiseSVN and login with ubuntu user and password...
has anyone tried to /done this?

thanks in advace!
Best regards,
GMX750.

---

### Post by GMX750 on 2010-10-12
[center]**[color=red]*bump*[/color]**
[/center]

---

### Post by GMX750 on 2010-10-12
Anyone?

---

### Post by luvshines on 2010-10-12
How did you configure against Active Directory ??
I mean are you using the method of adding winbind in nsswitch, PAM
Or, using likewise-open

---

### Post by GMX750 on 2010-10-12
> **luvshines said:**
> How did you configure against Active Directory ??
I mean are you using the method of adding winbind in nsswitch, PAM
Or, using likewise-open

```
I can access my repository via HTTP... it's standard apache configurations...
<Location /svn>
DAV svn
SVNParentPath /srv/repos/svn/repo1
....
```

I don't know how to do what *YOU* are asking.... lol
do you? xD

---

### Post by luvshines on 2010-10-12
> **GMX750 said:**
> Hi all. I've spent the last week googling for sollutions to my problem like crazy.. I decided that the best approach would be to register in a forum and explain my goal.

I have installed Turnkey Linux's Trac appliance. [COLOR="blue"]I have successfully setup my apache with active directory authentication.[/COLOR]

:lolflag: I was asking how did you accomplish this(marked in [COLOR="Blue"]BLUE[/COLOR])

---

### Post by GMX750 on 2010-10-12
> **luvshines said:**
> :lolflag: I was asking how did you accomplish this(marked in [COLOR=Blue]BLUE[/COLOR])

Oh ! ok.. lol
I followed this excellent tutorial:

```
http://www.jejik.com/articles/2007/06/apache_and_subversion_authentication_with_microsoft_active_directory/
```

hope it helps : D

---

### Post by luvshines on 2010-10-12
> **GMX750 said:**
> Oh ! ok.. lol
I followed this excellent tutorial:

```
http://www.jejik.com/articles/2007/06/apache_and_subversion_authentication_with_microsoft_active_directory/
```

hope it helps : D

Ah!! Looks like it is using Active Directory as LDAP only :D

Nice tutorial :KS

Coming back to your original issue, the subversion configuration which is described here isn't working for you ?

---

### Post by atworkwithjf on 2010-10-12
Likewise-open seems a little nicer way to solve this problem, especially if you use 6.0 or newer versions.  How married to the initial aproach are you?

---

### Post by luvshines on 2010-10-12
> **atworkwithjf said:**
> Likewise-open seems a little nicer way to solve this problem, especially if you use 6.0 or newer versions.  How married to the initial aproach are you?

@atworkwithjf

Although I have never worked with likewise-open, but seeing some other threads, it looks like a pretty easy and nice solution for configuring against AD

I have always stuck to old way of editing nsswitch, PAM files and then 'net ads join' :D

Can you give me a very brief idea of how likewise doesn't need to add winbind stuff in files. Does it work only on LDAP component of AD ? Also, does a single configuration enables AD authentication for all the services, viz - FTP, HTTP, SSH etc ?

I surely go to the official website to study. But was just asking a little kick-start from your side, towards the right direction. **Hope I am not asking too much** :D

---

### Post by atworkwithjf on 2010-10-12
@luvshines

Well, first and formost it allows you to accomplish all of what we're talking about here in one step instead of three

There are a host of cli tools which make management and debugging far less painful

It's open source, and there's an active community working on the codebase and supporting the users 

It correctly configures kerberos so kerberos aware apps actually work they way they're intended to (for me that's probably the biggest issue because after 20+ years on unix I still look at configuring krb5 as being one of the bigger pains).  Think NFS4 (krb5 auth), automount, etc.

About the only thing you need to do on a properly configured box is make sure your dns is working properly (i.e. resolvong your DC correctly) and fix the nsswitch.conf in 10.04 (it never even checks dns after failing to find mdns minimal):

```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

SHOULD READ:

hosts:          files mdns4_minimal [NOTFOUND=continue] dns mdns4

```There are also some useful tools for globally defining your user's shell, etc.

It's also RFC2307 compliant and does not require schema changes in AD which is a nice bonus.

_atworkwithjf

---

### Post by GMX750 on 2010-10-13
Well... the tutorial I showed was to provide authentication against AD but for users who try to acces my website.. not my svn repository.
I use TortoiseSVN to access it via svn+ssh. however, when I'm prompted for a username and password, I can only login with ubuntu users. My goal is to authenticate against AD when logging in to my svn repository.
I have tried to use lilkewiseopen.. but the tutorial I followed instructed me to do something like "ssh DOMAIN/user@DChostname"... but no succes with that.
I am able to successfully join my domain with likewiseopen, but I cannot login because "the server refused the connection on port 22"....
should I try something else?

---

### Post by GMX750 on 2010-10-13
[center][color=red]*bump*
[/color][/center]

---

### Post by luvshines on 2010-10-13
> **GMX750 said:**
> 
I have tried to use lilkewiseopen.. but the tutorial I followed instructed me to do something like "ssh DOMAIN/user@DChostname"... but no succes with that.
I am able to successfully join my domain with likewiseopen, but I cannot login because "the server refused the connection on port 22"....
should I try something else?

I don't think you'll be able to ssh at the DChostname.

Try:
```
ssh <AD-domain-name>\\<user-name>@<ip-of-svn-server>
```

Since you will have the SVN server machine configured against AD and you need to ssh to this server using AD credentials

---

### Post by GMX750 on 2010-10-13
you're right, i can now login using 

DOMAIN\\user@domain.local

however, after installing LikewiseOpen.. i'm unable to telnet, ssh, or svn+ssh to my ubuntu machine... probably because LikewiseOpen changes some important files like:
ssh_config
sshd_config
nsswitch.conf
resolve.conf
/etc/pam.d/*

etc..

does anyone know how to solve this issue?

Thank you

---

### Post by GMX750 on 2010-10-13
Bump

---

### Post by atworkwithjf on 2010-10-13
when you try to login are you prepending the domain to the username?

---

### Post by GMX750 on 2010-10-13
> **atworkwithjf said:**
> when you try to login are you prepending the domain to the username?

yes, when tortoiseSVN asks me for a login

I provide this as the username:

DOMAIN\\USER@domain.local

and the correct password, of course...

PuTTy gives me a message saying:
```
"PuTTy Fatal Error:
Software caused connection abort"
```

If I provide root as username
and my root pass as password, I get:
```
"PuTTy Fatal Error:
Server unexpectedly closed network connection"
```

I am able to login to my ubuntu machine via terminal, using an AD user...

---

### Post by luvshines on 2010-10-13
> **GMX750 said:**
> yes, when tortoiseSVN asks me for a login

I provide this as the username:

DOMAIN\\USER@domain.local

and the correct password, of course...

PuTTy gives me a message saying:
```
"PuTTy Fatal Error:
Software caused connection abort"
```

I am able to login to my ubuntu machine via terminal, using an AD user...

For putty, try domain\user only, ie. no \\ and no @domain.local

---

### Post by atworkwithjf on 2010-10-13
luvshines,

That's a good suggestion, I was about to suggest the same thing.

You may want to look at the documentation and configure your systems to use the assume default domain option to avoid having to do this.

- atworkwithjf

---

### Post by luvshines on 2010-10-13
@atworkwithjf

But as OP says that root cannot ssh, I can't see any reason why likewise would break that.

Does likewise change nsswitch and PAM files ?

---

### Post by atworkwithjf on 2010-10-13
pam is modified (obviously) by likewise.  Likewise does nothing to change the default behavior of Ubuntu regarding root logins.  You still need sudo to su - root.

---

### Post by luvshines on 2010-10-13
> **atworkwithjf said:**
> pam is modified (obviously) by likewise.  Likewise does nothing to change the default behavior of Ubuntu regarding root logins.  You still need sudo to su - root.

Ok, that looks good.

I was talking about Comment #18, where OP says that when i user root username and password for ssh through putty, it says connection closed by server.
AFAIK, local users will still be honored by the sytem, right ?

---

### Post by atworkwithjf on 2010-10-13
> **luvshines said:**
> Ok, that looks good.

I was talking about Comment #18, where OP says that when i user root username and password for ssh through putty, it says connection closed by server.
AFAIK, local users will still be honored by the sytem, right ?

Yes unless you explicitly configure your installation to prevent that.

---

### Post by btindie on 2010-10-13
There is a [patch]("http://code.google.com/p/openssh-lpk/") for openssh that allows you to store you're public key in an LDAP directory and authenticate using that.
 
Also, there's a document from Microsoft of all people on using [OpenSSH on Linux using Windows/Kerberos for Authentication]("http://port25.technet.com/Videos/research/OpenSSH%20on%20Linux%20using%20Windows.pdf") and also this on [Active Directory Integration]("http://blog.scottlowe.org/2007/01/15/active-directory-integration-index/").

---

### Post by bodhi.zazen on 2010-10-13
kerberos FTW !!!

Although , honestly, it is almost as easy to just use ssh keys.

---

### Post by GMX750 on 2010-10-14
Well, I know LikewiseOpen changese those files, however, my linux installation is Turnkey's Trac package. So the issue probably has to do with that...

---

### Post by GMX750 on 2010-10-14
I have 2 virtual machines running turnkey trac linux. one of them has LikewiseOpen installed, the other doesn't.
When I use putty or "shell in a box" to authenticate to the "likewiseopen machine" i get the same "connection refused" or "software unexpectedly closed network connection" messages.. I can only login via "shell in a box" in my browser.. either using domain account or machine account...

However, when I do the same on my other machine (without likewiseopen installation) I can successfully telnet, SSH, and use TortoiseSVN to access my SVN repositories.
I have tried outputting putty's log in an effort to debug the connection here's the most relevant parts:

I am using an active directory domain account as username like so

DOMAIN\\USER@domain.local (which works fine when authenticating via shell in a box)

INITIALIZING CONNECTION:

```
=~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2010.10.14 10:47:13 =~=~=~=~=~=~=~=~=~=~=~=
Event Log: Writing new session log (SSH packets mode) to file: putty.log
Event Log: Looking up host "10.150.1.74"
Event Log: Connecting to 10.150.1.74 port 22
Event Log: Server version: SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
Event Log: We claim version: SSH-2.0-PuTTY_Release_0.60
Outgoing packet type 20 / 0x14 (SSH2_MSG_KEXINIT)
```END OF CONNECTION:

```
Incoming packet type 60 / 0x3c (SSH2_MSG_USERAUTH_INFO_REQUEST)
  00000000  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
Outgoing packet type 61 / 0x3d (SSH2_MSG_USERAUTH_INFO_RESPONSE)
  00000000  00 00 00 00                                      ....
Outgoing packet type 2 / 0x02 [COLOR=Red](SSH2_MSG_IGNORE)[/COLOR]
  00000000  00 00 00 e0 a6 bd ca e2 8b 16 39 48 a0 97 65 9c  ..........9H..e.
  00000010  cb 03 84 fe b3 e3 22 db c3 c8 94 d3 c7 06 3e 65  ......".......>e
  00000020  96 e8 27 ab 2c c8 8a 88 5e a6 48 36 25 01 0f 6b  ..'.,...^.H6%..k
  00000030  93 87 67 32 0e 8b 67 1e e9 35 e6 c4 c6 6d 2c ad  ..g2..g..5...m,.
  00000040  5f 6a 6c da 22 3c 63 35 89 9f 59 ca 6d c6 0e db  _jl."<c5..Y.m...
  00000050  d9 d7 1d 28 49 7d c0 2f 85 2c 39 7e ed 35 48 59  ...(I}./.,9~.5HY
  00000060  c7 99 ff e9 39 94 86 ae 7e 30 70 04 b3 49 fb 62  ....9...~0p..I.b
  00000070  7e 45 f0 8b eb 28 d0 d2 59 0b 26 ff 19 32 54 ab  ~E...(..Y.&..2T.
  00000080  0e 41 ca 5d 56 83 7f c9 d7 53 f2 00 22 46 a0 99  .A.]V....S.."F..
  00000090  65 76 db 72 32 e1 c2 a3 55 bf 16 09 ea 4c 6a 70  ev.r2...U....Ljp
  000000a0  99 15 a8 7a 95 51 26 c1 67 6b 42 82 de 10 65 24  ...z.Q&.gkB...e$
  000000b0  1a be 84 0b a5 ab 2c 24 2e e2 fe d1 ca 92 57 80  ......,$......W.
  000000c0  de 48 15 e3 7e ef 6f b5 db 51 f4 1a 3a e8 83 c0  .H..~.o..Q..:...
  000000d0  16 21 16 40 86 ef ae 88 8b e8 58 10 4e 70 6f 3a  .!.@......X.Npo:
  000000e0  17 e4 d0 39                                      ...9
Incoming packet type 52 / 0x34 [COLOR=Red](SSH2_MSG_USERAUTH_SUCCESS)[/COLOR]
Event Log: Access granted
Outgoing packet type 90 / 0x5a [COLOR=Red](SSH2_MSG_CHANNEL_OPEN)[/COLOR]
  00000000  00 00 00 07 73 65 73 73 69 6f 6e 00 00 01 00 00  ....session.....
  00000010  00 40 00 00 00 40 00                             .@...@.
[COLOR=Red]Event Log: Network error: Software caused connection abort[/COLOR]

```this is a bit odd.. I get a MSG IGNORE (that may very well be unimportant or exteemely relevant.... : \)
and after that, as you can see I get SSH2_MSG_USERAUTH_SUCCESS
witch tells me that i've been sucessfully authenticated against... what? SSH? Active Directory?

P.S the error seems to be with putty I guess.... since Shell In a Box is a web based terminal emulator

---

### Post by luvshines on 2010-10-14
For Putty to connect to Likewise open machine, did you try username as 'domain\username' instead of 'domain\\username@local.domain'

---

### Post by GMX750 on 2010-10-14
> **luvshines said:**
> For Putty to connect to Likewise open machine, did you try username as 'domain\username' instead of 'domain\\username@local.domain'

I have now.. and I get the same error.
you see.. I can only authenticate to the likewiseOpen machine via browser Shell In A Box.
But with the other machine, i can authenticate via SSH, Shell In A Box and svn+ssh....

probably the issue is with the alterations that LikewiseOpen made to my SSH config Files??
I noticed the following lines in my sshd_config file... but don't know if it is normal or what:

```
#GSSAPI options
[...]
GSSAPIAuthentication yes
[...]
GSSAPICleanupCredentials yes

```and in ssh_config:

```
GSSAPIAuthentication yes
#Overwritten by lwidentity : GSSAPIDelegateCredentials no
GSSAPIDelegateCredentials yes
```I think I'm close to solving the issue.. since it clearly is LikewiseOpen who messed up my configuration..

any thoughts?

Thank you,
GMX750

---

### Post by GMX750 on 2010-10-14
[center][color=red]***bump***
[/color][/center]

---

### Post by GMX750 on 2010-10-14
[center][b][color=red]*bump*
[/color][/b][/center]

---

### Post by luvshines on 2010-10-14
> **GMX750 said:**
> 
I noticed the following lines in my sshd_config file... but don't know if it is normal or what:

```
#GSSAPI options
[...]
GSSAPIAuthentication yes
[...]
GSSAPICleanupCredentials yes

```and in ssh_config:

```
GSSAPIAuthentication yes
#Overwritten by lwidentity : GSSAPIDelegateCredentials no
GSSAPIDelegateCredentials yes
```I think I'm close to solving the issue.. since it clearly is LikewiseOpen who messed up my configuration..

any thoughts?

Thank you,
GMX750

GSSAPI configurations in sshd_config is normal.

For ssh_config the delegatecredentials has been changed but that file will come into effect when you are ssh from that machine to somewhere else, since it is a client file

For ssh to the the server itself, only sshd_file on the server side and ssh_config file on the client will come into picture

---

### Post by luvshines on 2010-10-14
Can you post the output of cat command on nsswitch.conf, /etc/pam.d/sshd and /etc/pam.d/common-auth and /etc/pam.d/common-account ?

---

### Post by GMX750 on 2010-10-14
of course, just tell me how to do that... :S

is it cat [filename] ?

thanks..

---

### Post by btindie on 2010-10-14
```
cat /etc/nsswitch.com
cat /etc/pam.d/sshd
cat /etc/pam.d/common-auth
cat /etc/pam.d/common-account
```

---

### Post by GMX750 on 2010-10-14
sorry, but I cannot copy text from shell-in-a-box... Here's some images uploaded to imageshack:
[http://img156.imageshack.us/img156/7285/sshd.png](http://img156.imageshack.us/img156/7285/sshd.png)
[http://img222.imageshack.us/img222/7599/commonaccount.png](http://img222.imageshack.us/img222/7599/commonaccount.png)
[http://img403.imageshack.us/img403/9838/commonauth.png](http://img403.imageshack.us/img403/9838/commonauth.png)
[http://img140.imageshack.us/img140/1259/nsswitch.png](http://img140.imageshack.us/img140/1259/nsswitch.png)

thanks

---

### Post by atworkwithjf on 2010-10-14
> **GMX750 said:**
> Well, I know LikewiseOpen changese those files, however, my linux installation is Turnkey's Trac package. So the issue probably has to do with that...

Before we start pointing at Likewise here (which you are are somehow claiming is the source of some misery) let's actually try and debug the issue.  Integrating a linux box into an AD domain is no trivial task and I think you may have yourself all tied up here with a misconfigured authentication components which all rely on each other for proper functionality.  Hopefully you didn't go ahead and take btindie's suggestion and start patching ssh and further complicating your issue.

The only question I have before we continue is, 'is the machine you are working with a production machine and do you have the luxury of starting over?'  

Given all the different methods you've tried to employ here to skin this cat it may be simpler for everyone to just start from scratch and employ a single solution that meets your authentication requirements with one package.

After all the changes you made to your config to get basic LDAP authentication working and then slapping Likewise atop that it's anyone's guess what's going on on your system.

What you are trying to accomplish is not in any way unusual but I think it's important to get his working one step at a time.

---

### Post by luvshines on 2010-10-14
> **GMX750 said:**
> sorry, but I cannot copy text from shell-in-a-box... Here's some images uploaded to imageshack:
[http://img156.imageshack.us/img156/7285/sshd.png](http://img156.imageshack.us/img156/7285/sshd.png)
[http://img222.imageshack.us/img222/7599/commonaccount.png](http://img222.imageshack.us/img222/7599/commonaccount.png)
[http://img403.imageshack.us/img403/9838/commonauth.png](http://img403.imageshack.us/img403/9838/commonauth.png)
[http://img140.imageshack.us/img140/1259/nsswitch.png](http://img140.imageshack.us/img140/1259/nsswitch.png)

thanks

I am bit stumped here since lot of PAM authority has been given to pam_lwidentity.so, can't find much documentation for it :(

Can you check what logs are produced in auth.log for the machine users when you try to login. I hope there is auth.log in /var/log , since I am not familiar with Turnkey

---

### Post by GMX750 on 2010-10-14
Hi, yes Turnkey has /var/log/auth.log...
I'm not at work right now, but I can tell you that the logs are something like this:

```
...
attempting to retrieve password (0x000000)
request failed
unable to open env file /etc/default/locale no such file or directory
user root is not known
...
```

the logs weren't displayed in this order, but the main idea is there.
I managed to fix the "unable to open file" issue by using the "update-locale" command
which created a blank file in "/etc/default/" containing only a commented line.

"root is not known", but I don't get that error for my domain user... so that's a minor problem.

Tomorrow I'm going to try and install likewiseOpen in a new machine and instead of using my own account, I'll try using another one with permission to add computers to my domain.. I suspect that was the initial problem....
however, tomorrow I'll try and post some of the most relevant logs (since auth.log is a bit huge..)

thank you for the help so far!
I'll keep you posted

P.S: those logs are related to SSH connections!

---

### Post by GMX750 on 2010-10-14
> **atworkwithjf said:**
> Before we start pointing at Likewise here (which you are are somehow claiming is the source of some misery) let's actually try and debug the issue.  Integrating a linux box into an AD domain is no trivial task and I think you may have yourself all tied up here with a misconfigured authentication components which all rely on each other for proper functionality.  Hopefully you didn't go ahead and take btindie's suggestion and start patching ssh and further complicating your issue.

The only question I have before we continue is, 'is the machine you are working with a production machine and do you have the luxury of starting over?'  

Given all the different methods you've tried to employ here to skin this cat it may be simpler for everyone to just start from scratch and employ a single solution that meets your authentication requirements with one package.

After all the changes you made to your config to get basic LDAP authentication working and then slapping Likewise atop that it's anyone's guess what's going on on your system.

What you are trying to accomplish is not in any way unusual but I think it's important to get his working one step at a time.

Hi, thanks for the reply. Let me try to explain myself better:

I have 2 virtual machines, one with and the other without likewiseOpen.

**the one without likewiseopen allows me to:**

```
use Shell-In-A-Box to login to my ubuntu machine with root account.
use SSH to acces my server via PuTTy.
use svn+ssh to acces my svn repository via TortoiseSVN.
```**The one with likewiseOpen allows me to:**

```
use Shell-In-A-Box to login to my ubuntu machine using a domain or root account.
```So i think it's pretty obvious that the issue was caused by LikewiseOpen, since both machines are exactly identical copies of each other.
I may be wrong.. but I'm almost sure that the problem was caused by my LikeWiseOpen installation

---

### Post by atworkwithjf on 2010-10-14
> **GMX750 said:**
> So i think it's pretty obvious that the issue was caused by LikewiseOpen, since both machines are exactly identical copies of each other.
I may be wrong.. but I'm almost sure that the problem was caused by my LikeWiseOpen installation

I have a dozen VM's here running LWO without any issue whatsoever (from 9.04 to 10.04 both i386 and x64 and a half dozen other distros to boot), so I'm highly suspicious of your configuration. 

 How far from the default configuration is your machine.  i.e. if I install and update ubuntu on a box how much difference would there be between our boxes?

What you don't realize is that Ubuntu has their own pam modification mechanisms (pam-auth-update) and it tries to deal with things that have been modified outside this mechanism but you can't account for every possible tweak users may make to their pam stack.  For this reason, Likewise makes use of these tools so when making changes to the pam configuration your machine doesn't end up in these kind of states.

Since you have already made changes to your config without any use of or reliance on auth-pam-update (as indicated in the first page of this thread), one can only guess what might be going on.  This is precisely why I suggested you go back to a fresh install or a snapshot of this machine before you went about tinkering with all this.

---

### Post by atworkwithjf on 2010-10-14
FYI - [http://www.likewise.com/community/index.php/forums/viewannounce/863_38/](http://www.likewise.com/community/index.php/forums/viewannounce/863_38/)

---

### Post by GMX750 on 2010-10-20
Thank you for all your advice, suggestions and solutions provided. As I suspected, the issue was solved by providing authentication to my website, and svn repository via HTTP access and apache LDAP configuration for multiple domain authentication, and svn repository authorization setup. LikewiseOpen was not the sollution, nor the problem I guess.

---

### Post by atworkwithjf on 2010-10-20
FYI - [http://www.likewise.com/community/index.php/forums/viewthread/829/](http://www.likewise.com/community/index.php/forums/viewthread/829/)

---

