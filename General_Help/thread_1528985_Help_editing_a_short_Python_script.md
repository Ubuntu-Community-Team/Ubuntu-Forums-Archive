---
title: "Help editing a short Python script"
date: 2010-07-11
forum: General Help
---

### Post by cj.surrusco on 2010-07-11
I need some help with the python script for a program called InfoPane (a system monitor screenlet). I installed this program today, and it monitors all disks that are mounted in the system. However, I only want it to monitor two specific file systems.

The two file systems that I want it to monitor are /dev/md0 and /dev/sdb1 mounted at / and /media/Data, respectively.  

I have excerpted what I believe is the part of the program's .py script that controls the disk monitoring. 

Would it be possible to alter this script so that only / and /media/Data are monitored?

Any insight whatsoever is greatly appreciated. Thanks.

```
 ##############################
    #####        DISKS       #####
    ##############################
    elif sensor == 'disks' and self.ifRefresh( sensor, '3sec' ):
      list = sensors.disk_get_disk_list()

      self.disks = []
      for disk in list:
        disk = sensors.disk_get_usage(disk)
        if self.disksType == 'usage':
          self.disks.append( {
            'name' : disk[0],
            'capacity' : disk[1],
            'usage' : disk[2],
            'free' : disk[3],
            'usage%' : disk[4].replace( '%', '' ),
            'free%' : str( 100-float( disk[4].replace( '%', '' ) ) ),
            'mount' : disk[5],
          } )
        elif self.disksType == 'free':
          self.disks.append( {
            'name' : disk[0],
            'capacity' : disk[1],
            'usage' : disk[3], # in usage is free
            'free' : disk[2], # in free is usage
            'usage%' : str( 100-float( disk[4].replace( '%', '' ) ) ), # in usage is free
            'free%' : disk[4].replace( '%', '' ), # in free is usage
            'mount' : disk[5],
          } )

      if self.disks == self.disksOld and not self._allUpdate:
        return False
      self.disksOld = self.disks

      return True
    # end disks
```

---

### Post by oldfred on 2010-07-11
I only know enough python to be dangerous.

list = sensors.disk_get_disk_list()

You can hardcode this entry or modify the sensors.disk_get_disk_list() which must search for the drives & return a list.



#list = sensors.disk_get_disk_list()
[COLOR=DarkRed]# print "list is ", list[/COLOR]
I do not know exact format is uses??
list = ('/dev/md0',  '/dev/sdb1')
or perhaps with or without ' ??
list = ((/dev/md0),  (/dev/sdb1))

To debug something like this I add a print statement and run it with geany to see what it prints so I know what to use. Then I comment it back out so I can use it later if need be. Added with comment above.

---

### Post by cj.surrusco on 2010-07-11
> **oldfred said:**
> I only know enough python to be dangerous.

list = sensors.disk_get_disk_list()

You can hardcode this entry or modify the sensors.disk_get_disk_list() which must search for the drives & return a list.



#list = sensors.disk_get_disk_list()
[COLOR=DarkRed]# print "list is ", list[/COLOR]
I do not know exact format is uses??
**list = ('/dev/md0',  '/dev/sdb1')**
or perhaps with or without ' ??
list = ((/dev/md0),  (/dev/sdb1))

To debug something like this I add a print statement and run it with geany to see what it prints so I know what to use. Then I comment it back out so I can use it later if need be. Added with comment above.

The bold method above worked perfectly. Thanks a lot for the help. I am starting to learn python, but I am just a beginner at the moment, so I needed that tip. Thanks again.

---

