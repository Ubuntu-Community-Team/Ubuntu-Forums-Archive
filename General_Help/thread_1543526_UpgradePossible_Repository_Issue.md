---
title: "Upgrade/Possible Repository Issue"
date: 2010-08-01
forum: General Help
---

### Post by sdmike6 on 2010-08-01
Everytime I update my computer with ubuntu 10.04 I get this message(pic is attached).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=165152&d=1280660746[/IMG]

This is one error message I get:

[B]```
GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 620396F19C0042C8Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg  Something wicked happened resolving 'download.skype.com:http' (-5 - No address associated with hostname)
Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/lucid/Release.gpg  Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)
Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz  404  Not Found [IP: 204.9.165.83 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```[/B]


I have used UbuntuTweak and Ailurus to add some repositories so I'm not sure if one of those are affecting this.

What steps should I follow to fix this?

Thanx :)

---

### Post by Scooter_X on 2010-08-01
I have the same sortof thing... maybe the suggestion in a [thread]("http://ubuntuforums.org/showthread.php?t=1543327&highlight=address+hostname") of mine that I started yesterday could help you? It didn't seem to work for me, but you never know, one could get lucky. It's driving me bonkers. Both times I've tried to upgrade to Lucid I've had some kindof crazy issue.

---

### Post by snowpine on 2010-08-01
System->Software Sources and disable all the 3rd party repos/PPAs.

---

### Post by Scooter_X on 2010-08-01
> **snowpine said:**
> System->Software Sources and disable all the 3rd party repos/PPAs.

Well I quit gotting the error, so that's good. I guess I knew that one of my ones that was screwing up, dropbox.com, was 3rd party. One that was having issues was *[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu). *I figured it was an official repository. Do you by chance know what that repository is for? It's labeled 'Lucid Partner'. ... Anyway, that helped me to understand what was going on a bit better. I wasn't really needing updates to dropbox anyway. Plus I had installed from a .deb, I don't know why it was listed under 3rd party... do some packages automatically add themselves?

Well thanks for the help, I at least appreciate it. Hope sdmike6 can benefit from it as well.

---

### Post by sdmike6 on 2010-08-04
Thank you for the help! :)

---

