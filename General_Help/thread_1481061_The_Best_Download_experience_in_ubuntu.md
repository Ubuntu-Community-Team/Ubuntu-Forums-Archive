---
title: "The Best Download experience in ubuntu"
date: 2010-05-12
forum: General Help
---

### Post by AndrewSimoes on 2010-05-12
For some reason, my downloads on Windows are really slow no matter what download accelerator I use. I've tried IDM, FDM , DAP , DAM , Orbit , Supersonic , jDownloader - they all have some problem . Sometimes the files just halt and refuse to be downloaded.

WARNING : NOT FOR ADVANCED USERS!!

On Ubuntu though I have found a wonderful solution that sees me all the time maxing out my download connection and often exceeding it with absolutely no problems.

Here's the combination :
Aria 2 + Flashgot.
I will show you how to set it up, how to configure it and how to pause , resume downloads.
That's all one needs! 

1. To get started , let's download Aria 2.
 
 Fire up a terminal and enter 

```
sudo apt-get install aria2
```2. And now Flashgot : Install the add-on from this site:

 [http://flashgot.net/](http://flashgot.net/)

 Close Firefox

3. Now to choose Aria 2 as the default download manager 
   Open Firefox 
   Tools
   Flashgot -> More Options -> General Tab and select Aria 2.

4. Now in terminal :
    ```

    cd 
    mkdir .aria2
   
```   Now create a file called aria2.conf inside .aria2( which is a hidden folder can be 
     viewed by pressing Ctrl+H in the Home Folder)
   ```
 
    cd .aria2
    gedit aria2.conf
   
```
5. Open the file and type split=100 on the first line.

That does it . Now to download anything  say for example a video from youtube :

[http://www.youtube.com/watch?v=x6Kq0qMMpgU](http://www.youtube.com/watch?v=x6Kq0qMMpgU)

in the bottom right corner click the flashing icon ( Flashgot Media) or alternatively go to Tools->Flashgot->Flashgot Media

6. Your download will start after selecting a download folder. A window will open which will display progress. To Pause , press Ctrl+C.

7. To resume open History, navigate to the page and again click 'Flashgot Media' 
The file will resume.

---

### Post by --[zyro]-- on 2011-02-12
hello... i m a newbie in ubuntu...this is not working ... i hv done all the things as u said ...but still youtube videos are downloading with only 5 connections....plz suggest some corrections to increase the no. of connections in aria2 + flashgot...

---

