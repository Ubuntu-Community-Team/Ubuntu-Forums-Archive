---
title: "Ubuntu and eggdrop!"
date: 2006-02-21
forum: General Help
---

### Post by GTX on 2006-02-21
Hello You lot,

I have been trying to get eggdrop to work properly for the past 4-5 hours.

When I configure the eggdrop everything works fine, The eggdrop will not start without -n (debug mode) added to the command line, This displays everything which is going on,.

If I just type ./eggdrop -m bla.conf the eggdrop will say its booted but will not! It wont connect or telnet.

Im quite advanced on things with eggdrop but I have no idea what is coursing this.

As long as the eggdrop is in debug mode it works fine no problems, if its not it doesnt. You might think this isnt a problem but it is because Im going to be running alot of eggdrops and do not want to have to use screen all the time

It just doesnt seem to like going into a background process.

Now the intresting thing is here, I did apt-get install eggdrop just to see if it had the stuff complied differently which it did to a certain degree and I nicked /usr/bin/eggdrop and called it something else on my username.

Intresting it booted the eggdrop without -n but when I typed commands it crashed, Probaly a problem with the binarys.

I also need to complie it manualy as I have to enable some extra features in the source code so a precomplied source wont be any good for me.

I realy hope you guys can help me fix this, This is the only problem I have had on ubuntu!

Edit: I Dont think this is a problem with the eggdrop, I think its to do with ubuntu someway or another, because it works fine on Fedora Core 3 exactly the same setup.

Thanks,
Charlie :mrgreen:

---

### Post by GTX on 2006-02-21
Can someone PLEASE help :confused:

---

### Post by GTX on 2006-02-22
This problem has been solved,

Just for you who have this problem to heres how to fix it.

Type in console: sudo apt-get install eggdrop

Then go back into your normal user account and type: wget [http://ftp.debian.org/debian/pool/main/e/eggdrop/eggdrop_1.6.17.orig.tar.gz](http://ftp.debian.org/debian/pool/main/e/eggdrop/eggdrop_1.6.17.orig.tar.gz)
tar -zxvf eggdrop_1.6.17.orig.tar.gz
cd eggdrop_*

Now just configure it to how you like.

Once configured go back to your home directory and go into the eggdrop folder then type:

rm -rf eggdrop
sudo cp -r /usr/bin/eggdrop /home/yourusername/eggdrop/
sudo chown username:username eggdrop

Then you should be able to run eggdrop without having to have -n on the end.

Hope this helps some of you

---

### Post by raven65az on 2006-12-12
hmm...config file not found

---

### Post by Raff7 on 2007-08-18
> **GTX said:**
> Hello You lot,

I have been trying to get eggdrop to work properly for the past 4-5 hours.

When I configure the eggdrop everything works fine, The eggdrop will not start without -n (debug mode) added to the command line, This displays everything which is going on,.

If I just type ./eggdrop -m bla.conf the eggdrop will say its booted but will not! It wont connect or telnet.

Im quite advanced on things with eggdrop but I have no idea what is coursing this.

As long as the eggdrop is in debug mode it works fine no problems, if its not it doesnt. You might think this isnt a problem but it is because Im going to be running alot of eggdrops and do not want to have to use screen all the time

It just doesnt seem to like going into a background process.

Now the intresting thing is here, I did apt-get install eggdrop just to see if it had the stuff complied differently which it did to a certain degree and I nicked /usr/bin/eggdrop and called it something else on my username.

Intresting it booted the eggdrop without -n but when I typed commands it crashed, Probaly a problem with the binarys.

I also need to complie it manualy as I have to enable some extra features in the source code so a precomplied source wont be any good for me.

I realy hope you guys can help me fix this, This is the only problem I have had on ubuntu!

Edit: I Dont think this is a problem with the eggdrop, I think its to do with ubuntu someway or another, because it works fine on Fedora Core 3 exactly the same setup.

Thanks,
Charlie :mrgreen:
same problem but with the last version .18, nobody know how to fix?

---

