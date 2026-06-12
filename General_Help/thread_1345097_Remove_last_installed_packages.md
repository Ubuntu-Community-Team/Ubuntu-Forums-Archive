---
title: "Remove last installed packages"
date: 2009-12-03
forum: General Help
---

### Post by ArielEnter on 2009-12-03
OK, forget a bout all this. See the newest posts.
> 
I was looking for a good substituted to Movie maker in Ubuntu by installing and trying many options I found in the repository using the Synaptic Package Manager. When I tried to uninstall them back, I notice that all the required dependencies installed with the program stayed intact. Since all those dependencies were installed only for us to be able to use that specific program, we probably wont be needing them for anything else either.

So how do you solve this problem? Well as far as I know there isn't a easy way yet.  [lalejand]("http://brainstorm.ubuntu.com/contributor/lalejand/") propose to add that function to the Synaptic Package Manager ([http://brainstorm.ubuntu.com/idea/19003/](http://brainstorm.ubuntu.com/idea/19003/)). Until this feature is added to the Synaptic, I thought on a way to do it and I wanted to shared with the forum.

Go to the Synaptic Package Manager then in the menu File>History. This history keeps track of the actions you have made in the Synaptic. Find out which one of those shows the actions taken to install that specific program. You'll find a list of all installed packages in the installation process. Select them all, copy and paste them to OpenOffice Writer. Now we will try to make all that list into one line command. First of all, we will take all the parenthesis enclosed information out, to do this, you will go to edit>Find & Replace. Then you write the following in the "Search for" area: \(.{0,}\)
You leave blank the "Replace with" area. Next, you click on More Options and check "Regular expression". Finally you will click on "Replace All".
Now all what's left is exclusively the name of the packages. 
To make it a one line command you will use again the Find & Replace just changing the "Replace with" area with the following symbol: $
You click "Replace All" again and now we have a one line list of all packages. We will add the following code to make it a one line command: sudo apt-get --purge remove

Once that that is done, go to File>Export and save the file as a html. You will be required to install openoffice-java-common for this. Now, the reason you are doing this last step is because, for some reason, when you copy and paste from OpenOffice.org to the terminal, this last one doesn't take it as a one line string, don't know why, but you can check it out by pasting the code in gedit, you will see that for some reason the list is divided in multiple lines again.

So once you saved the file as a html file, you will open it using your web browser, select everything and know paste it in the terminal and run it. That's it.

If any body has an easier way to do this I'll love to hear his/her opinion. See you all.

Example:

From this

akonadi-server (1.2.1-0ubuntu4)
akregator (4:4.3.2-0ubuntu6)
amarok (2:2.2.0-0ubuntu2)
amarok-common (2:2.2.0-0ubuntu2)
amarok-utils (2:2.2.0-0ubuntu2)
apport-kde (1.9.3-0ubuntu4.1)
apturl-kde (0.4.1ubuntu2)
ark (4:4.3.2-0ubuntu1)
cdrdao (1:1.2.2-18ubuntu3)

to this

                                 apt-get --purge remove akonadi-server  akregator  amarok  amarok-common  amarok-utils  apport-kde  apturl-kde  ark  cdrdao


---

### Post by marshmallow1304 on 2009-12-03
```
sudo apt-get --purge autoremove
```


> 
autoremove is used to remove packages that were automatically
installed to satisfy dependencies for some package and that are no
more needed.

---

### Post by ArielEnter on 2009-12-04
You were right :shock: But whats the meaning of following thread then?
[http://ubuntuforums.org/showthread.php?t=95881&highlight=uninstall+kubuntu-desktop](http://ubuntuforums.org/showthread.php?t=95881&highlight=uninstall+kubuntu-desktop)

Oh, I get it, kubuntu-desktop installs multiple applications that are not dependences of it, but it includes those programs separately. That's why

sudo apt-get --purge autoremove 
doesn't work in that specific situation.

---

