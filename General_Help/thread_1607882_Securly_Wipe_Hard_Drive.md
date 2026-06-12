---
title: "Securly Wipe Hard Drive"
date: 2010-10-28
forum: General Help
---

### Post by gypsumwolf on 2010-10-28
```
sudo apt-get install wipe
wipe /dev/sda
```
```
sudo dd if=/dev/zero of=/dev/sda

```
```
sudo dd if=/dev/urandom of=/dev/sda
```

With a Ubuntu Server install CD there is an option to Erase the HDD in the partitioner.

Are there any other ways (with Linux)? I read somewhere its best to wipe it 8 passes because some powerful software may be able to retrieve data if it is less then 8.

---

### Post by mikewhatever on 2010-10-28
Shred can delete files securely. Look at 'man shred' for details.

---

### Post by matt_symes on 2010-10-28
Hi

You can also use dban to wipe drives

Kind regards

---

### Post by dcstar on 2010-10-29
> **gypsumwolf said:**
> 
..........
Are there any other ways (with Linux)? I read somewhere its best to wipe it 8 passes because some powerful software may be able to retrieve data if it is less then 8.

Total, unadulterated rubbish.

"Software" can only retrieve the last data written to any magnetic drive. The "theoretical" ability to somehow read overwritten magnetic data locations has only been "demonstrated" in movies and TV crime shows.

For about the last 20 years hard drive technologies encode what is actually written to the magnetic surface, so even sending zeroes to the drive ends up as various patterns on the actual surface which are then converted back to zeroes when read.

People still quote methods for now ancient hard drive technologies and people still make money out of products that have no relevance these days (like the Guttman method that the author even says is no longer valid). If you really want to "wipe" a drive, download the NIST tool which uses the inbuilt ATA "Secure Erase" command that all modern hard drives have and use that or just do one dd pass of any pattern whatsoever.

---

### Post by Irony on 2010-10-29
Personally I use shred;

```
sudo shred -vfz -n 1 /dev/sdb3
```

The command above does 1 pass of randomisation and then one pass of zeros.

I'm not sure of the logic of doing multiple passes - I assume that if one scrambles all the magnetic dipoles of a disc in one pass then the data is gone.

Note this is done on an unmounted partition.

---

