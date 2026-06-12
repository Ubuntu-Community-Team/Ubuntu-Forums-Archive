---
title: "Can't keep Matlab Application in Launcher"
date: 2012-03-01
forum: General Help
---

### Post by kroeze on 2012-03-01
I tried clicking "Keep in Launcher" for Matlab in the Launcher and when I log off it disappears, and if I close Matlab and try clicking on the icon in the Launcher Matlab won't boot. I tried several things suggested on other forums.

```
sudo wget http://upload.wikimedia.org/wikipedia/commons/2/21/Matlab_Logo.png -O /usr/share/icons/matlab.png 
``````
sudo wget 'https://help.ubuntu.com/community/MATLAB?action=AttachFile&do=get&target=matlab-r2011a.desktop' -O /usr/share/applications/matlab.desktop
```Which didn't work for me. I also tried 

```
gedit /usr/share/applications/matlab.desktop
```and then editing the exec line to 

```
Exec=/usr/local/MATLAB/R2011a/bin/matlab -desktop
```As other information for me to run Matlab I do 

```
cd /usr/local/MATLAB/R2011a/bin
``````
./matlab
```

---

