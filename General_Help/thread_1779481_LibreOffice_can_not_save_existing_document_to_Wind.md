---
title: "LibreOffice can not save existing document to Windows server"
date: 2011-06-10
forum: General Help
---

### Post by advimac on 2011-06-10
I am having a problem with a LibreOffice when saving or saving as to a Windows Share.  
 

 Configuration:
 iMac running Ubuntu 11.04 – new install
 

 Network
 Small office server running Windows. Mounted using the Gigolo manager (used without issue in version 10.10).
 

 All of our contracts and proposals are on the server. I can open a contract in LibreOffice from the server. (All documents I am working with are native openoffice formats, these were not MS file conversions. )
 

 I open a document titled “A_Libreoffice_test.odt” from the contracts directory on the windows server. No problems. I save as “A_Libreoffice_test_2.odt” to the contracts directory on the Windows server and get this error box:
 

 LibreOffice 3.3
 Error saving the document A_Libreoffice_test:
 General error.
 General input/output error
 

 If I select all contents within my document and paste it into a new LibreOffice Writer file then save the new file to the contracts directory on my Windows server, it saves without any problems. However, should I open that very same file that I just created and try to save it after a change or save as without any change, I will receive the error again.
 

 Of course copy and pasting textual contracts is one thing but we also do all of our proposals in OpenOffice Draw (LibreOffice Draw) which behaves the same way. The select all, copy/paste into a new document workaround is less attractive in Draw.  
 

 We have 5 Ubuntu machines in our office working with files on this server. For now, employees and I are having to save our documents and transfer them to the server nightly.
 

 I did a test by booting into the MacOS where I am also running LibreOffice and did not experience the same problem.  
 

 Here is what I have tried so far:
 

 1) Removing all libreoffice applications and files then reinstalling but that also did not solve the problem.  
 

 2) Disabling the firewall on our Windows server temporarily to test the save as function (no change).
 

 3) Remove libreoffice and try to install OpenOffice (not successful).
 

 4) Poured some scotch and posted this question here on the Ubuntu forum... hopefully this works :)
 

 Any help is appreciated.

---

### Post by advimac on 2011-06-14
I discovered a workaround if anybody is having the same problem. I downloaded the most recent OpenOffice Windows application then installed it using Wine. By running the Windows OpenOffice in Wine on my Ubuntu 11 install I can access documents on the server, save, save as, etc, without any problems. The saving takes a couple seconds longer but I have noticed this to be common when running applications in Wine.

---

### Post by protonpusher on 2011-06-15
I've recently started a similar thread going over at the Libreoffice site ([http://www.libreoffice.org/get-help/nabble-mailing-list-interface/):]("http://www.libreoffice.org/get-help/nabble-mailing-list-interface/%29:") Look for "Generalinput/output error when saving to network drive."  Can't say that a good solution has turned up though, although I may try the wine workaround. The machine with the problme is  a pc running Ubuntu 11.04. I have an old mac G4 with Ubuntu 10.04, and it works well with the shares. 

Any idea if this affects Libreoffice only, or does it affect OOo as well?

I am very new to Ubuntu (and Linux), but one thought I had was to try to get to the share though a link, but I get an error when I try to set up the link (something about file type not supported).

---

### Post by chris-desford on 2011-06-20
Having just upgraded to Ubuntu 11.4 and thereby LibreOffice, I have discovered the same problem. I can open a network location (outside LO), double click on a file - and it will open LO successfully. 

However, if, from within LO, I navigate to a network location and try and load a file, nothing happens. If I try to save a file to a network location, I get the error <<Error saving the document ***** General Error. General Input/output error>>
I would add that this is despite the Save dialogue box within LO having allowed me to create a new folder to put the file in - so I am presuming this can't be a network issue.

I can save a document from for example gedit with no errors - so again it does not seem to be a network/permissions issue.

Help please!

(b.t.w. - tried the LibreOffice location and it seems to be  a broken link)

---

### Post by tsagi on 2011-06-25
I am having the same problem here.

---

### Post by rod40cool on 2011-07-20
I'm having the same problem too, but I think I've found a work-around which is easy and doesn't require using the Windows version of LibreOffice under Wine.

Try this.


[LIST=1]
[*]In Libre Office goto the Tools|Options menu
[*]On the left, expand **LibreOffice**
[*]Click on **General**
[*]On the right hand side, select the "**Use LibreOffice dialog**s" under the heading **Open/Save dialog**s.
[*]Ok
[*]Try a Save As to a Windows network drive.
[/LIST]
This works for me without LibreOffice prompting for authentication

Must be something to do with the way LibreOffice talks to Nautilus for Samba shares. (my guess).
Hope this helps people

---

### Post by tsagi on 2011-07-23
the last one didn't work for me. I get the same error...:S

---

### Post by mariourk on 2011-09-21
I have the same problem. No solution yet? :(

---

### Post by paped on 2011-10-15
I have been having a similar issues i.e. cannot open then edit and save a network drive based file, cannot save a new office file to a network drive and in addition some other applications cannot save directly either even though I have full access via the file manager. After doing a bit of reading there appears to be a few issues around lock files etc in Office but one issue appears to be that Gnome uses GVFS so the network shares or drives are not really mounted as such and the directory that the shares appear in is hidden (.gvfs in the users home directory) which some applications do not seem to understand. I found a post (thank you to the poster - closed my browser for testing and cannot find it again to link on to this post) with the following fix and it seems to correct all my issues with Office and Firefox by allowing me to directly open, edit and save files to the network share (within Ubuntu 11.10). What I did:

1) Go to file manager (Nautilus) and enable viewing of hidden files.
2) In your home directory find the .gvfs directory and right click it then select "Make Link", this will create another directory called "linked to .gvfs" rename this to something useful - e.g. "network drives".
3) Log-on to the network share/drive as normal, this will show the drive/share in the left hand file manager pane as normal and in the linked directory that you have just created.
4) When you want to open, edit or save anything to the network drive go to your home directory, then the new linked "network drives" directory and the actual network drive/share name within it, rather than the direct drive/share link in file manager.

This appears to work for me tried in with a few downloads and documents....

Hope it helps....

---

### Post by kelyga on 2011-10-20
I'm using Mint 11 and faced the same problem with LibreOffice.

Thanks to paped proposed solution now I have the workaround.
That helped.
Indeed, this a little bit annoying to save the files through several additional mouse clicks. Still this is much better than nothing.

---

### Post by kimda on 2011-11-03
I've had the same problem. Another solution is to install the following package.

```
libgnomevfs2-extra
```

After installation logout and login again. Open the share via nautilus to have it mounted. Now you can save the file. The only problem is that you will have to give your username/password once everytime you login for your session. But after that you can just save documents to shares. 

I wonder why libreoffice has to have its own way to save files and cannot be just like gedit or abiword and use the gnome defaults this is really annoying.

---

### Post by ianc1 on 2011-11-07
I have managed to solve this on my machine although the credit should not go to me I got the solution on the LibreOffice forum after posting there (many thanks to Tom and Alex for their help).  Unfortunately I cannot find the original post again.

The issue is to do with file lock, which I assume is LibreOffice ensuring that it and only it has access to the file.

The solution is as follows and I hope it helps someone:

Open the file /usr/bin/soffice```
sudo gedit /usr/bin/soffice
```and find the line starting ```
# adjust environment
```I run LibreOffice 3.4.3 and this is line 87.

Comment out the entire of the if statement starting ```
if [ -z "$SAL_ENABLE_FILE_LOCKING" ]; then
```which for version 3.4.3 is lines 89-123.  Finally save the file.

After this all should work fine.

---

### Post by diversecg on 2011-11-28
I am experiencing this problem also, workstation is Ubuntu 11.10, LO 3.4.4 b402, I am unable to save any new documents from LO to a network share (Ubuntu server 10.04 with latest Samba 3.4.7, strict locking=yes, sync always=yes, oplocks=no).  I have tried the work around above with no effect.  I am however able to save documents already existing on server once opened, and LO locking options appear to make no difference.

Just a note on the work around of removing locking checks from /usr/bin/soffice may not be the best solution either (if it works for some people).  It would be better to edit config file which has less chance of overwrite on update, /etc/libreoffice/soffice.sh and set FILE_LOCKING=no

There are no errors on the server when this happens, and only other observed potential issue is that even with file locking set to no, LO still tries to create .lock files on the server, maybe it is trying to create this but does not see it created yet?  I could potentially test this by enabling sync always/strict sync on samba, but would be horrible for performance/usability of all shared files.

too bad the LO error dialog isn't a bit more detailed

---

### Post by Krondaj on 2012-02-08
Hi,

This worked for me Thanks kimda!!!

> **kimda said:**
> I've had the same problem. Another solution is to install the following package.

```
libgnomevfs2-extra
```

After installation logout and login again. Open the share via nautilus to have it mounted. Now you can save the file. The only problem is that you will have to give your username/password once everytime you login for your session. But after that you can just save documents to shares. 

I wonder why libreoffice has to have its own way to save files and cannot be just like gedit or abiword and use the gnome defaults this is really annoying.

---

### Post by Nhorning on 2012-03-20
> **rod40cool said:**
> I'm having the same problem too, but I think I've found a work-around which is easy and doesn't require using the Windows version of LibreOffice under Wine.

Try this.


[LIST=1]
[*]In Libre Office goto the Tools|Options menu
[*]On the left, expand **LibreOffice**
[*]Click on **General**
[*]On the right hand side, select the "**Use LibreOffice dialog**s" under the heading **Open/Save dialog**s.
[*]Ok
[*]Try a Save As to a Windows network drive.
[/LIST]
This works for me without LibreOffice prompting for authentication

Must be something to do with the way LibreOffice talks to Nautilus for Samba shares. (my guess).
Hope this helps people

This worked for me.  Thanks, it saved a ton of time.

---

