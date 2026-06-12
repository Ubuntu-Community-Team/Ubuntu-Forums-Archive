---
title: "Tomboy crashes on startup"
date: 2009-10-19
forum: General Help
---

### Post by HankB on 2009-10-19
Tomboy crashes on startup. Result of 
```
hbarta@bonsai:~$ tomboy >/tmp/tomboy.error.txt  2>&1
```

(after editing to delete hundreds of duplicated lines) is

```
hbarta@bonsai:~$ cat /tmp/tomboy.error.txt  
[INFO]: Initializing Mono.Addins
Stack overflow in unmanaged: IP: 0x81a64ef, fault addr: 0xbf23affc
Stack overflow in unmanaged: IP: 0x81a64ec, fault addr: 0xbf23affc
ERROR: Add-in root index is corrupt. The add-in database will be regenerated. (The requested operation caused a stack overflow.)
ERROR: Could not read folder info file (The requested operation caused a stack overflow.)
ERROR: Unexpected error in setup process (Object reference not set to an instance of an object)
ERROR: Add-in scan operation failed. The Mono runtime may have encountered an error while trying to load an assembly.
ERROR: Add-in root index is corrupt. The add-in database will be regenerated.
System.Exception: System.StackOverflowException: The requested operation caused a stack overflow.
  at (wrapper managed-to-native) System.IO.MonoIO:Read (intptr,byte[],int,int,System.IO.MonoIOError&)
  at System.IO.FileStream.ReadData (IntPtr handle, System.Byte[] buf, Int32 offset, Int32 count) [0x00000] 
  at System.IO.FileStream.RefillBuffer () [0x00000] 
  at System.IO.FileStream.ReadByte () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.ReadNext () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
<<<<<<<<<<<<<<<<<<<<<<< 992 idenntical lines deleted >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
Using assembly reflector: Mono.Addins.CecilReflector.Reflector
ERROR: Could not read folder info file
System.Exception: System.StackOverflowException: The requested operation caused a stack overflow.
  at (wrapper managed-to-native) System.IO.MonoIO:Read (intptr,byte[],int,int,System.IO.MonoIOError&)
  at System.IO.FileStream.ReadData (IntPtr handle, System.Byte[] buf, Int32 offset, Int32 count) [0x00000] 
  at System.IO.FileStream.RefillBuffer () [0x00000] 
  at System.IO.FileStream.ReadByte () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.ReadNext () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
<<<<<<<<<<<<<<<<<<<<<<< 992 idenntical lines deleted >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
ERROR: Unexpected error in setup process
System.Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Addins.Database.AddinDatabase.InternalScanFolders (IProgressStatus monitor, Mono.Addins.Database.AddinScanResult scanResult) [0x00000] 
  at Mono.Addins.Database.AddinDatabase.ScanFolders (IProgressStatus monitor, Mono.Addins.Database.AddinScanResult scanResult) [0x00000] 
ERROR: Add-in scan operation failed
Stack overflow in unmanaged: IP: 0x81a64ef, fault addr: 0xbf23afec
ERROR: The add-in database could not be updated. It may be due to file corruption. [COLOR="Red"]Try running the setup repair utility[/COLOR]

Unhandled Exception: System.InvalidOperationException: Extension node not found in path: /Tomboy/ApplicationAddins
  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Tomboy.AddinManager.InitializeMonoAddins (System.String old_conf_dir) [0x00000] 
  at Tomboy.AddinManager..ctor (System.String tomboy_conf_dir, System.String old_tomboy_conf_dir) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 
hbarta@bonsai:~$ 
```

There is a suggestion to [COLOR="Red"]Try running the setup repair utility[/COLOR] but I have no idea how to do that.

I've renamed the .tomboy directory and it seems to make no difference. The crash occurred under Jaunty and seems to remain with Karmic.

Suggestions on how to resolve would be appreciated.

thanks,
hank

---

### Post by scouser73 on 2009-10-19
You could try deleting your Tomboy profile, that is assuming you have your tomboy notes backed up elsewhere.  Go to your home directory, press **CTRL & H** and delete the folder **.tomboy**

---

### Post by HankB on 2009-10-21
> **scouser73 said:**
> You could try deleting your Tomboy profile, that is assuming you have your tomboy notes backed up elsewhere.  Go to your home directory, press **CTRL & H** and delete the folder **.tomboy**
Thanks - did that already and it made no difference.

-hank

---

### Post by directhex on 2009-10-21
Which release are you running?

Have you ever done anything odd with how your partitions are mounted?

From your stack trace, it looks like Mono's I/O module is failing when trying to read some kind of file (either the extensions, or stuff in your home folder)

---

### Post by HankB on 2009-10-21
> **directhex said:**
> Which release are you running?

Have you ever done anything odd with how your partitions are mounted?

From your stack trace, it looks like Mono's I/O module is failing when trying to read some kind of file (either the extensions, or stuff in your home folder)
This is on Karmic. It did the same on Jaunty.  I have / and /home partitions and a bunch of stuff in tmpfs:

```
hbarta@bonsai:~/Music$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              3874076   3001496    675788  82% /
udev                   1026660       256   1026404   1% /dev
none                   1026660       196   1026464   1% /dev/shm
tmpfs                  1026660     11876   1014784   2% /tmp
none                   1026660        92   1026568   1% /var/run
none                   1026660         0   1026660   0% /var/lock
none                   1026660         0   1026660   0% /lib/init/rw
/dev/sdb1             15512328   7137344   7587000  49% /home
tmpfs                  1026660         8   1026652   1% /var/tmp
tmpfs                  1026660       904   1025756   1% /var/log
```

Do you think the stack overflow is the result or the cause of the file I/O problem?

thanks,
hank

---

### Post by directhex on 2009-10-21
> **HankB said:**
> Do you think the stack overflow is the result or the cause of the file I/O problem?

thanks,
hank

The result. The stack overflow is happening in unmanaged (C) code, meaning that it's the Mono runtime itself which is behaving funny, for whatever reason

What kind of CPU do you have?

It might help if you talk to the #tomboy folks on GIMPnet, who can talk you through generating useful debug output

---

### Post by HankB on 2009-10-21
> **directhex said:**
> The result. The stack overflow is happening in unmanaged (C) code, meaning that it's the Mono runtime itself which is behaving funny, for whatever reason

What kind of CPU do you have?

It might help if you talk to the #tomboy folks on GIMPnet, who can talk you through generating useful debug output
This is an Atom (Asus Eee PC 901)

I did that (chat) and they asked that I capture output running 'tomboy --debug' and that seemed to fix the problem.

thanks,
hank

---

### Post by tuanndh on 2009-10-23
Can you share your solutions! pls, i've got the same trouble but i cann't connect to irc :-S

run tomboy with --debug options dont give useful info!

---

### Post by HankB on 2009-10-23
> **tuanndh said:**
> Can you share your solutions! pls, i've got the same trouble but i cann't connect to irc :-S

run tomboy with --debug options dont give useful info!
I ran 'tomboy --debug' twice and that seemed to clear up the problem. I had previously renamed the ~/.tomboy file. That's all I did.

-hank

---

