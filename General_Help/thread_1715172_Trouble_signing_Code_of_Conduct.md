---
title: "Trouble signing Code of Conduct"
date: 2011-03-26
forum: General Help
---

### Post by wanderingarticfox on 2011-03-26
I finally got around to getting an Open PGP Key but have had trouble signing the Ubuntu Code of Conduct in LaunchPad. At first I thought it was because I still had my 'Documents' Folder and the file 'Properties' still open so I closed them and have the same results. I have double checked the folder and the label and by the way I did not assign the double .txt extension. Below are the terminal out puts:

            :~$ gpg --clearsign UbuntuCodeofConduct-1.1.txt.txt

You need a passphrase to unlock the secret key for
user: "James L. Pond (2.75 years and still learning) <enviropond@roadrunner.com>"
2048-bit RSA key, ID 0B72A5B6, created 2011-03-26

gpg: gpg-agent is not available in this session
gpg: can't open `UbuntuCodeofConduct-1.1.txt.txt': No such file or directory
gpg: UbuntuCodeofConduct-1.1.txt.txt: clearsign failed: file open error
             :~$ gpg --clearsign UbuntuCodeofConduct-1.1.txt.txt

You need a passphrase to unlock the secret key for
user: "James L. Pond (2.75 years and still learning) <enviropond@roadrunner.com>"
2048-bit RSA key, ID 0B72A5B6, created 2011-03-26

gpg: gpg-agent is not available in this session
gpg: can't open `UbuntuCodeofConduct-1.1.txt.txt': No such file or directory
gpg: UbuntuCodeofConduct-1.1.txt.txt: clearsign failed: file open error
              :~$ 
I of  course removed my system name from before ;~$ for security purposes.
The file name I will copy and paste here: 
       gpg --clearsign UbuntuCodeofConduct-1.1.txt.txt
That is directly from the properties dialog box of the folder.
 I would appreciate help of any type. I imaginge it is something simple but as I say in my PGP Key 2.75 still learning :)

---

### Post by Krytarik on 2011-03-26
Although I have really no clue what you are doing here, may it be that you have one excess ".txt" in your filename?:
```
:~$ gpg --clearsign UbuntuCodeofConduct-1.1.txt[COLOR=Red]**.txt**[/COLOR]
```**EDIT:** I just yet noticed your remark about it. How about the path?

---

### Post by bkratz on 2011-03-26
See this page

[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

towards the bottom should be of interest-- example---

Validation on Launchpad
You need to tell Launchpad about your OpenPGP key(s) to be able to sign the Ubuntu Code of Conduct (and thus become an Ubuntero) and to build packages using HCT.

O

---

### Post by wanderingarticfox on 2011-03-27
Thx bkratz; I have bookmarked that page to study, sounds like something there will help after a quick glance; I'll report back once I  get things fixed so it can help others.

---

### Post by wanderingarticfox on 2011-03-29
I tried dropping the extra.txt; no joy so I cleared the folder and download folder and re-downloaded and still no joy.
I have been going  through the GPG How-to and have my Key, it is now showing on Launchpad; success with setting my key as default in ~/.bashrc and following commands in How-To; success with the encryption and creating revocation key/cert.
Trouble trying to make ASCII armored version of my public key and I entered the 'Uploading key to Ubuntu key-server' so I'm guessing I need to let that peculate.
Trouble still with the clearsign action in terminal

  ~$ gpg --clearsign UbuntuCodeofConduct-1.1.txt

You need a passphrase to unlock the secret key for
user: "James L. Pond (2.75 years and still learning) <enviropond@roadrunner.com>"
2048-bit RSA key, ID 0B72A5B6, created 2011-03-26

gpg: can't open `UbuntuCodeofConduct-1.1.txt': No such file or directory
gpg: UbuntuCodeofConduct-1.1.txt: clearsign failed: file open error
------------------------------------------------------------------------

Making an ASCII armored version of key

          ~$ sudo gpg --output mykey.asc --export -a OB72A5B6
[sudo] password for artis: 
gpg: WARNING: unsafe ownership on configuration file `/home/artis/.gnupg/gpg.conf'
gpg: WARNING: nothing exported

------------------------------------------------------------------------
Any help or clarification of what I am doing wrong or need to do; the plus side is I am finally getting use to the terminal a little but I do not have the background to develop my own inquiries.
I'm just trying to get to where I can do the "Getting Your Key Signed" portion of the How-To; I live in Niagara Falls NY and I'm willing to catch a metro bus to UB if needed to get verified and signed :)

---

### Post by t0p on 2011-03-29
I might be right off the mark here: but are you absolutely sure that the file (UbuntuCodeofConduct-1.1.txt or UbuntuCodeofConduct-1.1.txt.txt) is actually in the directory you are working in?

This is easily discovered by typing in the command:

```

ls

```

The output of that command will be a list of the contents of your working directory (ie. the directory you are in when you are trying to run commands).  If the file UbuntuCodeofConduct-1.1.txt (or UbuntuCodeofConduct-1.1.txt.txt) does not appear in that list, this means you are not running the terminal commands in the correct directory.  When you downloaded the file, it probably went to the ~/Downloads directory; so you need to switch to that directory by running the command:

```

cd ~/Downloads

```

Now run the *ls* command again.  Does the file appear in the list?  If so, you are now in the correct directory and your gpg commands should work.

I apologise if I'm totally off the mark here.  But this is the only reason I can think of why you would get the error message that the file does not exist.

---

### Post by wanderingarticfox on 2011-03-30
Thx for the info; going to look at this I think you might just be teaching me something here:)
Ok, Well that got me started now I am Lost again. I found the file as cd ~/Documents and it generated the .txt.asc file but I can  not open it; well I have tried the open with 'File Browser; Archive Manager; Auto-run and Document Viewer [not in that order but those are the ones I've tried] and I need to open it to copy and paste in>

Sign the Ubuntu code of Conduct

To sign the code of conduct:

   1.

      Download the file to your own computer and read it carefully to ensure you agree to it.
   2.
      In a terminal, run the command:

          gpg --clearsign UbuntuCodeofConduct-1.1.txt 

      (or whatever filename you gave to the code). This will create a file with a name like UbuntuCodeofConduct-1.1.txt.asc.
   3.

      Open that new file, and copy and paste its contents into this box. Then click &#8220;Continue&#8221;.

Signed Code:
  I cannot seem to open so I can copy and paste here

Terminally challenged>>>>Help Please.

---

