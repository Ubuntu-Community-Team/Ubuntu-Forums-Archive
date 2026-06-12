---
title: "SVN Server"
date: 2011-04-26
forum: General Help
---

### Post by tomfpotter on 2011-04-26
Not sure if the problem is actually my svn server or not - here is the scenario so hopefully someone can clarify it for me:

1) I configured my svnserver per this [site]("https://help.ubuntu.com/community/Subversion") - I used the "Micha&#322; Wojciechowski Blog post" towards the bottom of the page for additional setup - on my linux machine which runs  bare bones (non 64 bit) 

2) On my Vista machine I installed Eclipse Helios 64 bit and Java SDK 64 bit. I also got subclipse running in eclipse and followed the [these ]("http://subclipse.tigris.org/wiki/JavaHL")and [these ]("http://www.ibm.com/developerworks/opensource/library/os-ecl-subversion/")instructions for getting the necessary JavaHL for working with the 64 bit.

3) I was able to verify that subclipse was working by checking out subclipse from the instructions from [this ]("http://www.ibm.com/developerworks/opensource/library/os-ecl-subversion/")site (starting at figure 8).

4) I was able to verify that the subversion server was running with the "nmap localhost" command (svn was running on port 3690 - its default port) and I was able to check out a test project using the "svn" command.

When I try to map the svn repository on the remote machine from eclipse on my Vista machine (SVN Repositories -> New -> Repository Location... -> svn://192.168.1.103:3690) eclipse hangs for a few seconds and then issues the error: Error validating location:"org.tigris.subversion.javahl.ClientException:Couldn't find a repository  svn:No repository found in 'svn://192.168.1.103'" (my linux box is on my home network as machine 192.168.1.103). 

Any clue as to what my problem could be . . . I assume it is my client (as that is what the exception seems to indicate) and possibly my svnserver setup.

Thanks for your patience!

- Tom

---

