---
title: "Help installing Sottify in Linux"
date: 2010-08-28
forum: General Help
---

### Post by laser101uk on 2010-08-28
Hi Guys, I am very new to Linux, I am likely to need lots of help. The area confuses me the most is installing software. I have ubuntu 10.4 installed and I am trying to install spotify. It all seems to go ok until I get to the install part when I am getting this in Terminal

spotify-client-gnome-support is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  spotify-client-qt: Depends: libqt4-dbus (>= 4.5.0) but it is not installable
                     Depends: libqt4-webkit (>= 4.5.0) but it is not installable
                     Depends: libqtcore4 (>= 4.5.0) but it is not installable
                     Depends: libqtgui4 (>= 4.5.0) but it is not installable
E: Broken packages


I have been following these instructions

 				So how do you get it?  We’ve packaged the first release as a Debian Squeeze/Ubuntu 10.04 package. 			
 			 			# 1. Add this line to your list of repositories by 
#    editing your /etc/apt/sources.list
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

# 2. Run apt-get update
# 3. (optional) If you want to verify the downloaded packages,
#    you will need to add our public key

gpg --keyserver wwwkeys.de.pgp.net --recv-keys 4E9CFF4E
gpg --export 4E9CFF4E |sudo apt-key add -

# 4. Run apt-get install spotify-client-qt spotify-client-gnome-support


I would be grateful for any help or advice....thanks

Steve

---

### Post by Smart Viking on 2010-08-28
Run these commands([COLOR=DarkRed]do not edit them![COLOR=Black])[/COLOR][/COLOR], write password when prompted.
```
sudo echo "deb http://repository.spotify.com stable non-free" >> /etc/apt/sources.list
``````
sudo apt-get update
``````
sudo apt-get install spotify-client-qt spotify-client-gnome-support
```As i said, do not edit them, **especially** not the first one!
These commands should do the work, run them and see if you can get spotify installed. :)

EDIT: Btw, the command to launch spotify is simply
```
spotify
```

---

### Post by lemino on 2010-08-31
I've done the same thing, it installs nicely and everything, but when I try to start it up I just get a segmentationsfault and nothing else. What can be done about this?

---

