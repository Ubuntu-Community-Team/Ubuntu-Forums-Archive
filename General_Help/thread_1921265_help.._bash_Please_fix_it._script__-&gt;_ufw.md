---
title: "help.. bash Please fix it. script  -&gt; ufw"
date: 2012-02-06
forum: General Help
---

### Post by oklokl on 2012-02-06
[http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution](http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution)
this Page Applications
 

Ubuntu 11.10 dvd 64bit 

#!/bin/bash
gnome-terminal -e "bash -c \"~/Folder/ufwblockrun.sh; exec bash\""

Click
Desktop -> sh file Button run





ufwblockrun.sh

#!/bin/bash
echo "ufw out blcok"
echo ""
echo "123.0.0.0/123.255.255.255"
echo ""
echo "sudo ufw reject out proto tcp from" 
echo ""
read -r -p "ip : " sam
read -r -p "ip : " sam2
echo ""
echo "passwords"
echo ""
    [[ -z $sam ]] && break
    [[ -z $sam2 ]] && break

sudo ufw reject out proto tcp from "$sam".0.0.0/"$sam2".255.255.255

    # Notifications:

    notify-send "block" "Folder: "$sam".0.0.0/"$sam2".255.255.255"
    printf 'block %s block ip OUT to TCP.\n' "$sam"

echo ""
echo ""
echo "### del ###"
echo ""
echo "sudo ufw status numbered"
echo ""
echo ""
echo "sudo ufw delete 42"
echo ""
echo ""
exit 0


--------------------------------------------------------
sudo ufw reject out proto tcp from **[COLOR=Red]45[/COLOR]**.0.0.0~55.255.255.255
Want
 Normal results

 but Result

block **[COLOR=Red]35[/COLOR]**.0.0.0.0~55.255.255.255 (The wrong value)
T^T Random .. error..

---

### Post by emiller12345 on 2012-02-07
I believe that 123.0.0.0/123.255.255.255 is not what your intending to do
123.0.0.0/255.0.0.0 is the correct way to represent the ip's from 123.0.0.0 to 123.255.255.255, but UFW will only recognize it in this format
**123.0.0.0/8**.  Heres some of the math to do this.
the 'Netmask' 255.0.0.0,  in base-16 is 0xFF000000, and in base-2 is 11111111000000000000000000000000
If we add the base-2 format 1+1+1+1+1+1+1+1 = 8


a second example, 123.0.0.0/255.128.0.0 -> 0xFF800000 -> 11111111100000000000000000000000
If we add the base-2 format 1+1+1+1+1+1+1+1+1 = 9
123.0.0.0/9
this is all the IP's in 123.0.0.0 to 123.127.255.255

so the line
```
sudo ufw reject out proto tcp from "$sam".0.0.0/"$sam2".255.255.255
```should probably be something like
```
sudo ufw reject out proto tcp from "$sam".0.0.0/8
```

---

### Post by oklokl on 2012-02-08
> **emiller12345 said:**
> I believe that 123.0.0.0/123.255.255.255 is not what your intending to do
123.0.0.0/255.0.0.0 is the correct way to represent the ip's from 123.0.0.0 to 123.255.255.255, but UFW will only recognize it in this format
**123.0.0.0/8**.  Heres some of the math to do this.
the 'Netmask' 255.0.0.0,  in base-16 is 0xFF000000, and in base-2 is 11111111000000000000000000000000
If we add the base-2 format 1+1+1+1+1+1+1+1 = 8


a second example, 123.0.0.0/255.128.0.0 -> 0xFF800000 -> 11111111100000000000000000000000
If we add the base-2 format 1+1+1+1+1+1+1+1+1 = 9
123.0.0.0/9
this is all the IP's in 123.0.0.0 to 123.127.255.255

so the line
```
sudo ufw reject out proto tcp from "$sam".0.0.0/"$sam2".255.255.255
```should probably be something like
```
sudo ufw reject out proto tcp from "$sam".0.0.0/8
```

Thank you so much .. :)
but..

sudo ufw reject out proto tcp from 123.0.0.0/145.255.255.255
I want ...

ex>
123~145.. 
123.124.125.126~... 145 block.. 255.255.255
123.0.0.0.0~123.255.255.255 block
124.0.0.0.0~124.255.255.255 block
~.. 145

---

### Post by emiller12345 on 2012-02-08
I wrote this script a while ago to help me understand how a netmask functions, and I think it might help you indirectly.  
[http://digitalmagican.wordpress.com/2011/07/07/maximum-and-minimum-ip-for-a-given-ipnetmask-combo/](http://digitalmagican.wordpress.com/2011/07/07/maximum-and-minimum-ip-for-a-given-ipnetmask-combo/)
it's two programs that go from 123.0.0.0/255.0.0.0 format to --> 123.0.0.1 ~ 123.255.255.254 format
(the end points of a netmask are usually reserved ip addresses, if you don't want that feature delete the line that mentions $DET)

what you really want is probably the exact opposite of those scripts.

---

### Post by emiller12345 on 2012-02-08
Or you could just use the same command over and over again like this
```

sudo ufw reject in from 123.0.0.0/8
sudo ufw reject out to 123.0.0.0/8
sudo ufw reject in from 124.0.0.0/8
sudo ufw reject out to 124.0.0.0/8
sudo ufw reject in from 125.0.0.0/8
sudo ufw reject out to 125.0.0.0/8
.
.
.
sudo ufw reject in from 144.0.0.0/8
sudo ufw reject out to 144.0.0.0/8
sudo ufw reject in from 145.0.0.0/8
sudo ufw reject out to 145.0.0.0/8

```

---

