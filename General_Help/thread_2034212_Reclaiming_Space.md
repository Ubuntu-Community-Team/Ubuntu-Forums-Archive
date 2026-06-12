---
title: "Reclaiming Space"
date: 2012-07-28
forum: General Help
---

### Post by czerdrill on 2012-07-28
I have a dual boot with Ubuntu and Mint right now, but I'm interested in getting rid of Mint as I don't like it as much as Ubuntu.  Question I have is how can I delete the Mint install and reclaim the partitioned space back to my Ubuntu install?

---

### Post by matt_symes on 2012-07-28
Hi

There are a number of ways for doing it but this is one method, where you keep the old partition as a storage partition.

1 Boot into you Ubuntu partition.
2. Start "disc utilty" from the dash.
3. Select the partition that contains Mint and format it.
4. Open a terminal and type

```
sudo update-grub
```

Enter your password. it will not be echoed to the screen. This will update grub and remove mint from the grub menu.

5. Optionally add the partition to fstab to automount it at boot.

Kind regards

---

### Post by czerdrill on 2012-07-28
thank you very much!

---

