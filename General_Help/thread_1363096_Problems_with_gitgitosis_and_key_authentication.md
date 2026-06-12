---
title: "Problems with git/gitosis and key authentication"
date: 2009-12-24
forum: General Help
---

### Post by ZeppelinJ0 on 2009-12-24
This is a repost from the Beginner forums, I feel this is a better forum for this question.

Hey everyone, looking for a little help as I've become pretty frustrated installing a remote git repository on my ubuntu server 9.10.

I'm following the directions posted here: [http://scie.nti.st/2007/11/14/hostin...and-secure-way](http://scie.nti.st/2007/11/14/hostin...and-secure-way)

The steps I've taken to get where I'm finding trouble are as follows:

1) I log in to my admin account (jdaily) on my "server" system where the remote git repositories will be held.

2) I create a folder called "src" in my home directory

3) I used git clone git://eagain.net/gitosis.git to download gitosis then use the python tools to install it

4) Next I create a user called 'git' by entering:
```

sudo adduser --system --shell /bin/sh --gecos 'git version control' --group --disabled-password --home /home/git git
```
5) Then I use "ssh-keygen -t rsa" to create a private and public key in /home/jdaily/.ssh/id_rsa(.pub)

6) From there I run the command 
```

sudo -H -u git gitosis-init < /home/jdaily/.ssh/id_rsa
This works fine
```

7) Here's where things go wrong. At this point the instructions say to input
```

git clone git@MYHOSTNAME:gitosis-admin.git

```

If I run this command from the server system (logged in as jdaily) I'm told to input a password for 'git.' However no password is supplied nor required so I'm just given a "Permission Denied(publickey, password)" error. If I try this from another machine, I'm given the same issue.


Sorry for the long-winded post, but does anyone have more detailed instructions on setting up and understanding a remote git repository? Or at least how to properly authenticate my SSH keys?

---

### Post by Nalroff on 2010-01-16
I'm having issues with this as well. Problem is, other user works, it just seems to be the git user and the auto-key moving command on the server that's making a problem. Any light on this yet?

Nalroff

---

### Post by Nalroff on 2010-01-21
Well I've fixed/found the problem. The syntax for the clone apparently needs to include the protocol and path to the folder with the repository. This may be just a workaround, but it works for me. Use:

```
git clone ssh://git@host/~/path/to/repositories/gitosis-admin.git
```

Thanks,
Nalroff

---

### Post by prefabSOFT on 2010-10-14
> **Nalroff said:**
> Well I've fixed/found the problem. The syntax for the clone apparently needs to include the protocol and path to the folder with the repository. This may be just a workaround, but it works for me. Use:

```
git clone ssh://git@host/~/path/to/repositories/gitosis-admin.git
```

Thanks,
Nalroff

Wow, thanks a lot for sharing this info! :)

This might get me on the right track fixing my issues.:guitar:

Well...at least my gitosis issues. :(

---

