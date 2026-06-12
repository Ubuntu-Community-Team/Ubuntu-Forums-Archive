---
title: "Encrypt tar &amp; Upload to Webdv"
date: 2012-02-24
forum: General Help
---

### Post by High Camp on 2012-02-24
Hi All,

I Googled and searched the tar man page but couldn't find what I need. 

I currently have a script that runs regularly to backup given folders in a tar.gz and upload to a Webdav. Being the paranoid risk manager that I am some suggested I should be encrypting backups before uploading them.

My current script simply does:
```

tar -pczf /my_docs/to_backup/www-`date +%y.%m.%d.%H00`.tar.gz /my_docs/www

```

I'm hoping there might be an option (i.e. -e) to encrypt the tar when it's created. Like I said, I couldn't find anything on the web about this. Everything I found is a gui or encrypts it after the fact.

The second part of my questions is, I'm looking for the command to automatically upload to a Webdav share. Again, I did a bunch of searching last night but couldn't find it. 

Help would be very much appreciated, thanks.

---

### Post by Paddy Landau on 2012-02-25
Regarding encryption, I don't ever recall seeing that option for tar.

However, have a look at gpg, which can encrypt a file for you. It should be installed by default on your system.

---

### Post by slavin on 2012-02-27
Hey Simon. Here's something simple that is a little more automated. 

It tars up all the files, then encrypts the tarball. 

The passphrase is embedded in the script, so it's fully automated and you could add this to a cron job.

I just used * when I tested it, but you can add your own path(s). My tar command is a bit different too. Feel free to customize of course. 

```
#!/bin/sh

echo Starting backup

FILE=`date +%y.%m.%d.%H00`-BACKUP.tar

# Create the tarball
echo creating $FILE
tar -cvf $FILE *

# Encrypt using GPG
gpg --no-use-agent --passphrase simons_password -c $FILE

# Cleanup
rm -f $FILE
```

Of course having the passphrase embedded is a bit of a security issue if someone ever hacked your linux server.

It's kinda crude, but will start you in the right direction.

Enjoy!!

Sean

---

### Post by Paqman on 2012-02-27
> **slavin said:**
> 
Of course having the passphrase embedded is a bit of a security issue if someone ever hacked your linux server.


Assuming the script was 700 then once someone has that level of access they can frolic around your server doing what they like anyway.

---

### Post by High Camp on 2012-02-29
Finally got a chance to look at this, thanks everyone for your help.

I came up with a related solution at the same time SLavin posted his but mine didn't use --no-use-agent. I ultimately used:
```

#!/bin/bash
FILES=/my_docs/to_backup/*
for f in $FILES
do
  gpg --no-use-agent --passphrase "ma_passphrase!" -c "$f"
  mv "$f" /tmp
done
exit 0

```

In the process I learned the following:
1.) Put "" around any file, if it has spaces in the name it'll fail out.
2.) Put "" around the passphrase because certain characters (! and &) will also cause it to fail.

It seems the Box.net's WebDav is unreliable at best so I'm not going to mess with automating the upload, I can live with doing that manually. So basically over the course of a week I copy anything important to the /to_backup folder and then I can encrypt and upload everything at once.

Hope that helps someone else,

---

