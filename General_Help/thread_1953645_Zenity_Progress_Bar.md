---
title: "Zenity Progress Bar"
date: 2012-04-06
forum: General Help
---

### Post by ukchris on 2012-04-06
Is it possible to combine this zenity progress bar:

```
zenity --progress --title="Getting MD5 Checksum" --pulsate --auto-kill --auto-close --text "It's doing it, alright?"
```

With this md5sum command? 

```
userfilemd5=$(md5sum $userfile | cut -d" " -f1)
```

Some of the files I check can take awhile as they are quite large and with no visual representation I could imagine someone else thinking the command isn't running.

I have tried a these and neither works:

```
userfilemd5=$(md5sum $userfile | cut -d" " -f1) | zenity --progress --title="Getting MD5 Checksum" --pulsate --auto-kill --auto-close --text "It's doing it, alright?"
```

```
(userfilemd5=$(md5sum $userfile | cut -d" " -f1)) | zenity --progress --title="Getting MD5 Checksum" --pulsate --auto-kill --auto-close --text "It's doing it, alright?"
```

And on it's own the md5 function works.

```
userfilemd5=$(md5sum $userfile | cut -d" " -f1) 
```

Obviously I am doing something work with piping one command into the next but I am not sure what?

Thanks in advance. :)

---

### Post by Habitual on 2012-04-06
I use yet Another Dialog, the zenity fork/successor and I have this snippet.

```

var1=`date`

yad --image=/home/jj/Documents/cirrhus9/Legal/cirrhus9_logo_blue.png --no-buttons --undecorated --skip-taskbar --timeout=2
function get_snapshots()
{
var3=`echo -n "FTB Snapshots="$(ec2-describe-snapshots -K /path/to/some/secret.pem -C /path/to/some/secret.pem --region us-west-1 | sort -r -k 5 | wc -l)`
}

touch /tmp/$$
( ( echo 1 ; while [ -f /tmp/$$ ] ; do sleep 1 ; done ; echo 100 ) | yad --progress --pulsate --auto-close --text="Counting Snapshots..." --width=150 --title="" --undecorated --no-buttons) & get_snapshots
rm /tmp/$$

#output
echo -e "$var1\n$var3"| yad --text-info --show-uri --width=300 --height=265 --center --name="EC2 Snapshots" --window-icon="/home/jj/Documents/favicon.ico" --button=Done
fi
fi

```

I hope that helps.

---

