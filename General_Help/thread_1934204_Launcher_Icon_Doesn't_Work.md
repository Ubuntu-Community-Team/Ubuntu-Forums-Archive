---
title: "Launcher Icon Doesn't Work"
date: 2012-03-01
forum: General Help
---

### Post by Kissell on 2012-03-01
I wanted to install Transmission Remote GUI, so I created and ran the following script.

```

# INSTALL TRANSMISSION REMOTE GUI
sudo add-apt-repository -y ppa:andreas-noteng/transgui
sudo apt-get -y update
sudo apt-get -y install transgui
sudo chmod 777 /usr/share/applications -R
echo "[Desktop Entry]" > /usr/share/applications/transmission-remote-gui.desktop
echo "Name=Transmission Remote GUI" >> /usr/share/applications/transmission-remote-gui.desktop
echo "GenericName=Transmission Remote GUI" >> /usr/share/applications/transmission-remote-gui.desktop
echo "X-GNOME-FullName=Transmission Remote GUI" >> /usr/share/applications/transmission-remote-gui.desktop
echo "Comment=Download and share files over BitTorrent" >> /usr/share/applications/transmission-remote-gui.desktop
echo "Exec=/usr/bin/transgui" >> /usr/share/applications/transmission-remote-gui.desktop
echo "Icon=transmission" >> /usr/share/applications/transmission-remote-gui.desktop
echo "Terminal=false" >> /usr/share/applications/transmission-remote-gui.desktop
echo "TryExec=/usr/bin/transgui" >> /usr/share/applications/transmission-remote-gui.desktop
echo "Type=Application" >> /usr/share/applications/transmission-remote-gui.desktop
echo "MimeType=application/x-bittorrent;x-scheme-handler/magnet;" >> /usr/share/applications/transmission-remote-gui.desktop
echo "Categories=Network;FileTransfer;P2P;GTK;" >> /usr/share/applications/transmission-remote-gui.desktop
echo "X-Ubuntu-Gettext-Domain=transmission" >> /usr/share/applications/transmission-remote-gui.desktop
echo "X-AppInstall-Keywords=torrent" >> /usr/share/applications/transmission-remote-gui.desktop
sudo chmod 644 /usr/share/applications -R

```

It installs, and I can run it from the command line with "/usr/bin/transgui &" as my user.  That works fine...  But when I click on the icon in the unity launcher, it just blinks and does nothing.  So I always have to start it from the terminal.

---

### Post by Kissell on 2012-03-01
Huh, I listed the permissions before doing this...  they were 644 in the applications folder for the files...  but I guess the folder itself should be 755.  

Opening it up fixes it... 
```
sudo chmod 777 /usr/share/applications -R
```

So it must be a permissions error on that folder.

---

