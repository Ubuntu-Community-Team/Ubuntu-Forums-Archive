---
title: "Signature Verification Failure"
date: 2010-05-11
forum: General Help
---

### Post by TheRealEdwin on 2010-05-11
I've searched and searched and my googlefu has failed me.

```
edwin@doomhammer:~$ sudo apt-get update
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US                                                                                                
Hit http://download.virtualbox.org lucid Release.gpg                                                                                                                                                          
Get:1 http://security.ubuntu.com lucid-security Release.gpg [189B]                                                                                                                                            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                                                                                                                                 
Get:2 http://us.archive.ubuntu.com lucid Release.gpg [189B]                                                                                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                                                           
Ign http://download.virtualbox.org/virtualbox/debian/ lucid/non-free Translation-en_US                                                          
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                                                              
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                                                                
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                                                              
Get:3 http://security.ubuntu.com lucid-security Release [32.5kB]                                                                                
Err http://security.ubuntu.com lucid-security Release                                                                                                   
  
Hit http://download.virtualbox.org lucid Release                                                                                                  
Hit http://download.virtualbox.org lucid/non-free Packages                                                                
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                         
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                                                                                                                                   
Get:4 http://us.archive.ubuntu.com lucid-updates Release.gpg [189B]                                                                                                                                           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                                                                                                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                                                                                                                           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                                                                                                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                                                                                                           
Get:5 http://us.archive.ubuntu.com lucid Release [57.2kB]                                                                                                                                                     
Err http://us.archive.ubuntu.com lucid Release                                                                                                                                                                
  
Get:6 http://us.archive.ubuntu.com lucid-updates Release [38.5kB]                                                                                                                                             
Hit http://archive.canonical.com lucid Release.gpg                                                                                                                                                            
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                                                                                                                      
Err http://us.archive.ubuntu.com lucid-updates Release                                                                                                                                                        
  
Hit http://archive.canonical.com lucid Release                                                                                                                                                                
Hit http://archive.canonical.com lucid/partner Packages                                                                                                                                                       
Get:7 http://dl.google.com stable Release.gpg [189B]                                                                                                                                                          
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US                                                                                                                                             
Get:8 http://dl.google.com stable Release [2,540B]                                                                                                                                                            
Get:9 http://dl.google.com stable/main Packages [904B]                                                                                                                                                        
Fetched 4,203B in 13s (316B/s)                                                                                                                                                                                
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
edwin@doomhammer:~$ sudo apt-get update > error
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Does anyone have a solution on how to fix this? This is on a clean install of 10.04.

---

### Post by dcstar on 2010-05-11
> **TheRealEdwin said:**
> I've searched and searched and my googlefu has failed me.
........
Does anyone have a solution on how to fix this? This is on a clean install of 10.04.

The "solution" is to use a different repository.

---

### Post by marvinptm on 2010-05-21
I had the same problam and found you need a new key for VB 3.2.

"Apparently VirtualBox 3.2 just got released, and it&#8217;s the first release under the Oracle name (since Oracle&#8217;s acquisition of Sun). As such, you need to get a new key:

wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

Problem solved. It then will let upgraded to 3.2&#8230;"

I found this info on xblurb from zeus77.

---

### Post by mwildam on 2010-05-25
> **marvinptm said:**
> ```

wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
```

I can confirm that this solves the problem - I already had updated to 3.2 and experienced the problem afterwards, but however.

---

### Post by earthbound01 on 2010-06-01
I entered "wget -q [http://download.virtualbox.org/virtu...racle_vbox.asc](http://download.virtualbox.org/virtu...racle_vbox.asc) -O- | sudo apt-key add -" into the terminal, and I got "gpg: no valid OpenPGP data found."

---

### Post by jewels. on 2010-06-03
> **earthbound01 said:**
> I entered "wget -q [http://download.virtualbox.org/virtu...racle_vbox.asc](http://download.virtualbox.org/virtu...racle_vbox.asc) -O- | sudo apt-key add -" into the terminal, and I got "gpg: no valid OpenPGP data found."

Agreed.  I am getting the same error.  I've googled to no solution.  

Here is my problem (just to verify that I'm having the same problem):

```
~$ sudo apt-get update
Get:1 http://download.virtualbox.org karmic Release.gpg [197B]
Get:2 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://download.virtualbox.org karmic/non-free Translation-en_US           
Get:3 http://download.virtualbox.org karmic Release [3,446B]                   
Get:4 http://dl.google.com stable Release [2,544B]


........ (it continues on.....)


Fetched 3,982B in 5min 33s (12B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://download.virtualbox.org karmic Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release  

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz  404  Not Found [IP: 204.9.165.83 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
~$ wget -q http://download.virtualbox.org/virtu...racle_vbox.asc -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.
~$

```

Strangely enough, I'm running Karmic Ubuntu 64 bit (not Lucid).
Anyone have any suggestions?
Thanks!

---

### Post by cesarse on 2010-06-03
Change ellipsis for [COLOR="Red"][FONT="Courier New"]albox/debian/or[/FONT][/COLOR]. URLs are not properly displayed here.

By the way, the "invalid signature" issue remains unsolved. It's Oracle's fault, not ours.

---

### Post by KayakJim on 2010-06-03
Running Ubuntu 9.10 Karmic 32-bit Desktop and also getting:
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>
when attempting to update the repository list.

---

### Post by jaygo on 2010-06-03
Looks like [this old fix]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

---

### Post by mercibe on 2010-06-04
Indeed, the old fix still does the trick...  Thank you very much!

---

### Post by Irregular Joe on 2010-06-04
I am on karmic, and even after adding the new key from the oracle_vbox.asc location, and doing the apt-get clean steps, I still get the message:

W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>

---

### Post by pleurastic on 2010-06-06
Thanks Jaygo.  You fixed mine.

---

### Post by pgonzamailcn on 2010-06-07
Thanks Jaygo. You fixed mine too.

---

### Post by Irregular Joe on 2010-06-07
I had to remove my apt.conf proxy before this would work properly for me.  Now it works, even after restoring the proxy configuration.  Thanks!

---

### Post by CeltaWeb on 2010-06-09
I haven't pulled this one out for a while but I can confirm it also worked for me. I add the following
```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

Then ```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
``` with sudo and it just finished updating.

Thanks I was hitting my head against a wall for a while on this one

---

### Post by fnord_ix on 2010-06-16
Thanks Jaygo.  Worked like a charm.

---

### Post by Orlic on 2010-06-22
> **jaygo said:**
> Looks like [this old fix]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```
Thank you very mich, this helped me to fix the problem

---

### Post by kflorek on 2010-06-25
"old fix" worked for me too. :popcorn:
I've been trying things for a solution for a while.

One of the things this does is change to the directory where the repo data is kept, move it to another name for backup, then recreate the directory, effectively deleting all the data. So be prepared for an hour download of all the data you removed if you are on dial-up.

 Might just doing this for the virtualbox repo with the error do the same thing?

---

### Post by cooltuyul on 2010-08-02
hmmmmm...

i, too, have that skype repo trouble and tried the good "old fix" but to no avail. 

the terminal gives me the same lines all the time, when using update manger and etc.

```
W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz  404  Not Found [IP: 212.72.53.130 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by schallstrom on 2010-08-10
> **jaygo said:**
> Looks like [this old fix]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

It works, thank you!

---

### Post by prokher on 2010-08-10
> **jaygo said:**
> Looks like [this old fix]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

thanks! works great!

---

### Post by buzzlightyear2 on 2010-10-01
I had to do this on lucid:

cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

---

### Post by m.maga on 2010-10-20
Thank You jaygo. It worked here for Ubuntu 10.10.

---

### Post by girishlc on 2010-11-24
>> wget –q "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xSHOULDBEYOURKEY" -O- | sudo apt-key add 

This works fine,
Give a try

Thanks to Jaiber,:)

-Girish.L.C

---

### Post by brasini on 2010-11-25
The old fix worked on 10.10 maverick meerkat here too but still a few issues:

I got '**Unknown id: cd**' when I used the **su cd /var/lib/apt** command, or **sudo: cd: command not found** when I tried **sudo cd /var/lib/apt**. 

So I typed this command without using **sudo** and got updates okay. I'm still getting the following GPG error at the end though:

**W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932**

I've probably missed something but not sure what. Any ideas? Thanks.

---

### Post by vietnux on 2010-11-27
> **jaygo said:**
> Looks like [this old fix]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```


error

Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://vn.archive.ubuntu.com](http://vn.archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

help me !!!

---

### Post by msambenny on 2010-11-30
> **jaygo said:**
> Looks like [this old fix]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```



Awesome this trick works smooth thanks a lot :)

---

### Post by zipizap on 2010-12-13
> **jaygo said:**
> Looks like [this old fix]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```


In my ubuntu 9.04 the above "old fix" solved the following error:

```

paulo@smsHub:~$ sudo apt-get update
[sudo] password for paulo:
Hit http://ppa.launchpad.net jaunty Release.gpg
Get:1 http://security.ubuntu.com jaunty-security Release.gpg [198B]
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://linux.dropbox.com jaunty Release.gpg
Hit http://es.archive.ubuntu.com jaunty Release.gpg
Hit http://ppa.launchpad.net jaunty Release
Get:2 http://security.ubuntu.com jaunty-security Release [57.9kB]
Err http://security.ubuntu.com jaunty-security Release

Hit http://ppa.launchpad.net jaunty/main Packages
Ign http://es.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://es.archive.ubuntu.com jaunty/restricted Translation-en_US
Hit http://ppa.launchpad.net jaunty/main Sources
Ign http://linux.dropbox.com jaunty/main Translation-en_US
Ign http://es.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://es.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://es.archive.ubuntu.com jaunty-updates Release.gpg
Hit http://linux.dropbox.com jaunty Release
Ign http://es.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://es.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Hit http://linux.dropbox.com jaunty/main Packages
Ign http://es.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://es.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://es.archive.ubuntu.com jaunty Release
Hit http://es.archive.ubuntu.com jaunty-updates Release
Hit http://es.archive.ubuntu.com jaunty/main Packages
Hit http://es.archive.ubuntu.com jaunty/restricted Packages
Hit http://es.archive.ubuntu.com jaunty/main Sources
Hit http://es.archive.ubuntu.com jaunty/restricted Sources
Hit http://es.archive.ubuntu.com jaunty/universe Packages
Hit http://es.archive.ubuntu.com jaunty/universe Sources
Hit http://es.archive.ubuntu.com jaunty/multiverse Packages
Hit http://es.archive.ubuntu.com jaunty/multiverse Sources
Hit http://es.archive.ubuntu.com jaunty-updates/main Packages
Hit http://es.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://es.archive.ubuntu.com jaunty-updates/main Sources
Hit http://es.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://es.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://es.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://es.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://es.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 199B in 4s (43B/s)
Reading package lists... Done
[COLOR=Blue]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: htt  p://security.ubuntu.com jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Sign  ing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems[/COLOR]

```Thanks jaygo :)

---

### Post by bookcrazy on 2011-01-27
> **CeltaWeb said:**
> I haven't pulled this one out for a while but I can confirm it also worked for me. I add the following
```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```Then ```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
``` with sudo and it just finished updating.

Thanks I was hitting my head against a wall for a while on this one
When I type in this old fix, I get this:

evan@Trigger-laptop:/var/lib/apt$ mv lists lists.old
mv: try to overwrite `lists.old/lists', overriding mode 0755 (rwxr-xr-x)? What should I do?

EDIT

I went System---->Administration---->Software Sources and changed Source code to "Main" 

I opened a terminal and entered

sudo apt-get update

and didn't get any errors.

---

### Post by mrojas73 on 2011-02-13
> **jaygo said:**
> Looks like [this old fix]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

That fixed my issue...thank you!

---

### Post by ccm.vslam on 2011-06-02
> **brasini said:**
> The old fix worked on 10.10 maverick meerkat here too but still a few issues:

I got '**Unknown id: cd**' when I used the **su cd /var/lib/apt** command, or **sudo: cd: command not found** when I tried **sudo cd /var/lib/apt**. 

So I typed this command without using **sudo** and got updates okay. I'm still getting the following GPG error at the end though:

**W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932**

I've probably missed something but not sure what. Any ideas? Thanks.

This looks awfully similar to the question asked [here]("http://ubuntuforums.org/archive/index.php/t-1221323.html"). Hope it helps.

---

### Post by AdrianTM on 2011-09-26
It looks like the problem happens so often that it's listed on VirtualBox download page. It happens regularly on my machine, does anybody have a clue why it happens?

---

### Post by Xillix on 2011-10-11
> **jaygo said:**
> Looks like [this old fix]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

Thanks this helped me, but I had to add "sudo" infront to get permission to do some of the above commands.

---

### Post by LnRSoft on 2012-01-09
Thanks! You saved my life Buddy! :popcorn:


> **jaygo said:**
> Looks like [this old fix]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

---

### Post by mackinna on 2012-02-23
The "old fix" just save my life thanks!!

---

### Post by wildmanne39 on 2013-04-25
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

