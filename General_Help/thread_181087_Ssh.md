---
title: "Ssh"
date: 2006-05-23
forum: General Help
---

### Post by Compact on 2006-05-23
I'm using a ubunu based pc renotely by using SSH. I want to download a file from internet using "wget". I want the computer to continus downloading the file even I exit from SSH. How could I do that?

---

### Post by paul.maddox on 2006-05-23
If you have screen installed then you can just run:
```
screen wget http://www.somewebsite.com/a_big_file.tar.gz
```

And press ctrl-a then d, this will detatch you from the screen session.
To resume the session later on just log back into ssh and type
```
screen -r
```


Or if you don't have screen, you could just send the process to the background using the following and checking the download.log file every so often for it's progress:

```
wget -o download.log http://www.somewebsite.com/a_big_file.tar.gz &
```

---

### Post by steve.horsley on 2006-05-23
The normal way is to launch the application with nohup (no hangup).  And use ampersand to put it in the background.  Thusly:
> nohup wget [http://whatever](http://whatever) &

Edit:
wget has a -b option that puts it in the background ant writes to a log file rather than stdout - that's probably a good one:
> nohup wget -b [http://whatever](http://whatever)

---

