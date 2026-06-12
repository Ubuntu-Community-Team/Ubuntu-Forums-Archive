---
title: "galaxium"
date: 2009-08-04
forum: General Help
---

### Post by shihkster1015 on 2009-08-04
I can not install galaxium on my computer for some reason
i had to use "sudo apt-get install galaxium-svn", which is messed up

---

### Post by y-lee on 2009-08-04
> **shihkster1015 said:**
> I can not install galaxium on my computer for some reason
i had to use "sudo apt-get install galaxium-svn", which is messed up


I am not sure what the problem is here, if you want help you are going to have to give us more information. How did ya try to install galaxium and what went wrong. Give details. As to use sudo apt-get ... how is that messed up? Did galaxium install but not work? whatever the issue you need to give details and specifics.

---

### Post by shihkster1015 on 2009-08-06
OK then...
First i added the galaxium repos.
Second i added the pubkey for galaxium (for some reason i had to do this for every third party software)
Third, i tried install galaxium by typing "sudo apt-get install galaxium" in Terminal, but it doesn't    
     work so i had to install by typing "sudo apt-get install galaxium-svn"
Then i got it to work, i can log in and i can see my contacts, but i can't chat
like when i double click a contact, nothing happens. And when i right click a contact, a little 5*20 comes up with nothing in it


BTW i can't seem to find the "create a new thread button" 
    where is it :P

---

### Post by y-lee on 2009-08-07
Ok I finally got around and installed galaxium and it acted much as you described. But i figured it out

at the bottom of galaxiums window after you're signed in there is  a button that says **All Sessions**. click it and change to whatever account you signed onto. Now you should be good to go.

---

### Post by y-lee on 2009-08-07
> **shihkster1015 said:**
> BTW i can't seem to find the "create a new thread button" 
    where is it :P

And oh the new thread button is on the main suport pages, such as [URL="http://ubuntuforums.org/forumdisplay.php?f=331"]general help 
[/URL] :D

---

### Post by shihkster1015 on 2009-08-07
Do you know what's up with the public key?
Everytime i insert a third party software, it will always say "Invalid Pub_key"
And this only started happening after Jaunty's release

---

### Post by shihkster1015 on 2009-08-07
> **y-lee said:**
> Ok I finally got around and installed galaxium and it acted much as you described. But i figured it out

at the bottom of galaxiums window after you're signed in there is  a button that says **All Sessions**. click it and change to whatever account you signed onto. Now you should be good to go.


It works perfectly now.
Thanks

---

### Post by kkkecw on 2009-12-02
I couldn't get it work
neither "galaxium-svn" nor "galaxium"
i added these repos.
deb [http://ppa.launchpad.net/galaxium/ubuntu](http://ppa.launchpad.net/galaxium/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/galaxium/ubuntu](http://ppa.launchpad.net/galaxium/ubuntu) hardy main

and then I did add the pubkey, but when I am trying to install it, it wouldn't find the packages

E: Couldn't find package galaxium-svn
E: Couldn't find package galaxium

---

### Post by ankspo71 on 2009-12-02
hi kkkecw,

I haven't used galaxium before, but have you updated your repositories after adding the repos to your repo  list? 

Try in the terminal
```
sudo apt-get update
```

then try to 
```
sudo apt-get install galaxium
```
or
```
sudo apt-get install galaxium-svn
```

Hope this helps,
James

---

### Post by kkkecw on 2009-12-06
ankspo71,
I did update the repos before installing
[U]
[/U][]("http://ohioloco.ubuntuforums.org/member.php?u=734190")

---

