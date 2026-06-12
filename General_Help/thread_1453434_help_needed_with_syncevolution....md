---
title: "help needed with syncevolution..."
date: 2010-04-13
forum: General Help
---

### Post by saidinesh5 on 2010-04-13
Hi guys did anybody succeed in setting up syncevo to sync their mobile phones?? i currently am on karmic... and i ve downloaded the binary from their website and used this to configure my phone

```

MacAddress=11:11:11:11:11:11
TEMPLATE=scheduleworld
B=syncevolution

$B --configure --sync-property syncURL=obex-bt://$MacAddress --sync-property enableWBXML=1 --sync-property remoteIdentifier='Test' --sync-property PeerIsClient=1 --sync-property username= --sync-property password= --template $TEMPLATE N70

$B --configure --source-property type=addressbook:text/x-vcard N70 addressbook
$B --configure --source-property type=calendar:text/x-vcalendar  N70 calendar
$B --configure --source-property type=calendar:text/x-vcalendar N70 todo

for i in calendar addressbook todo memo; do
  $B --configure --source-property uri=$i N70 $i
done

$B --configure --source-property type=virtual:text/x-vcalendar --source-property evolutionsource=calendar,todo N70 super

for i in calendar todo; do
  $B --configure --source-property uri=super N70 $i
done


```

the only thing that happens is :

```

[INFO] calendar+todo: inactive
[INFO] super: inactive
[INFO] contacts: inactive
[ERROR] caught signal 11, shutting down
Segmentation fault

```


this is my version information:
```

SyncEvolution 1.0beta2a
using libedataserver-1.2.so.11
using libebook-1.2.so.9
using libecal-1.2.so.7
using libecal-1.2.so.7
using libbluetooth.so.3
Loading backend library /usr/lib/syncevolution/backends/syncecal.so
Loading backend library /usr/lib/syncevolution/backends/syncxmlrpc.so
Loading backend library /usr/lib/syncevolution/backends/syncfile.so
Loading backend library /usr/lib/syncevolution/backends/syncaddressbook.so
Loading backend library /usr/lib/syncevolution/backends/syncmaemocal.so
Loading backend library /usr/lib/syncevolution/backends/syncsqlite.so
Loading backend library /usr/lib/syncevolution/backends/syncebook.so
```

---

