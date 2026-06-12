---
title: "Unable to execute add-apt-repository"
date: 2012-06-26
forum: General Help
---

### Post by mrfilbert on 2012-06-26
Every time I try to add a repository via add-apt-repository, I get the following error message:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (60, 'server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none')

Is there a way to remedy this?

---

### Post by jmfal on 2012-06-26
Welcome to Ubuntu

Are you tyoing the command into the terminal?
maybe you entered is incorrectly.

Copy/paste it and don't put the command prompt with the command:
Example of command>>>  jxxx@jxxx-2335111:~$

---

### Post by mrfilbert on 2012-06-26
This is the command I entered:

sudo add-apt-repository ppa:tldm217/tahutek.net

And this is the message I received back:


Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (60, 'server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none')

---

### Post by jmfal on 2012-06-26
I not sure whats wrong  it looks like its on the ppa side , maybe they entered something wrong or the servers are busy

---

### Post by josephmills on 2012-06-26
Try and add it the old school way. 

```
gksudo gedit /etc/apt/sources.list
```
add this to the bottom replacing 

YOUR_UBUNTU_VERSION_HERE
```

deb http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu YOUR_UBUNTU_VERSION_HERE main*
deb-src http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu YOUR_UBUNTU_VERSION_HERE main*

```
with you Ubuntu code name like if I was using 11.10 it would be 
```
deb http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu oneiric main 
deb-src http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu oneiric main 
```

Proff read then save the file and exit 
then in terminal 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AA71CF6C 


```
then 
```
sudo apt-get update
```

Is it there ?

---

### Post by philinux on 2012-06-26
> **mrfilbert said:**
> Every time I try to add a repository via add-apt-repository, I get the following error message:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (60, 'server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none')

Is there a way to remedy this?

If you want apt fast there is an official ppa.

 [http://iloveubuntu.net/apt-fast-164-released-fixes-and-proper-configuration-dialog](http://iloveubuntu.net/apt-fast-164-released-fixes-and-proper-configuration-dialog)

---

### Post by mrfilbert on 2012-06-26
I was able to install the software, but when I tried adding another repository, to test it out, I got the same error:


Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (60, 'server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none')

---

### Post by drmrgd on 2012-06-26
> **mrfilbert said:**
> I was able to install the software, but when I tried adding another repository, to test it out, I got the same error:


Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (60, 'server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none')

Looks like python-software-properties might be hosed.  Try reinstalling:

```
sudo apt-get --reinstall install python-software-properties

```

---

### Post by anewbie on 2013-02-07
Did this solve the issue? I have the same problem and it is very painful. I had to boot from usb stick to run something in java becauase I couldn't install orcale java :(
-
I've not been able to figure this one out but will try that last solution when i get home...

---

### Post by sandyd on 2013-02-07
CA Certificate chain of trust is probably broken

try
```

sudo apt-get --reinstall ca-certificates
sudo update-ca-certificates
```
to update your CA Certificates

---

### Post by anewbie on 2013-02-07
Sandy --

I tried that and no new certs were installed. When I did the reconfigure the only one i did not check was one that started with mozilla and had a lot of funny characters.

-----
Ok now that I'm home I've tried all the suggestions in this thread and none of them work :(
-
Maybe 12.04 is just broken ?

---

### Post by anewbie on 2013-02-08
One thing I should mentioned is that I was able to boot from a usb stick into 12.10 and use add-apt-repository fine (for the specific repositories I wanted to access). Is it safe for me to copy the certs from 12.10 and should I just assume that 12.04 is plain broken ?
-
I also tried deleting /etc/ssl/* and then reinstall ca-certificates from scratch but that also did not resolve the issue.

---

### Post by anewbie on 2013-02-10
Ok I found a fix for this problem and am posting it in case others have the same issue:

Note that 
apt-get --reinstall install ca-certificates
and
dpkg-reconfigure ca-certificates
by themselves did not fix the issue.

However:
rm -rf /usr/share/ca-certificates
followed by 
apt-get --reinstall install ca-certificates

does resolve the issue.
Since I blew away /usr/share/ca-certificates I cannot go back and figure out why reinstall did not resolve the issue but i have to guess maybe there was an old certificate that was causing an issue (not sure since /etc/ssl/certs/ca-certificates.crt was 1/2 the size it was prior to removing this directory and then reinstalling) (old size was 102637 and new size (now) is 233264)

---

