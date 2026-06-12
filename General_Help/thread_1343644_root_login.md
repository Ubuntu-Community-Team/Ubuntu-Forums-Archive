---
title: "root login"
date: 2009-12-02
forum: General Help
---

### Post by bulls_eye on 2009-12-02
i dont know really how to put this
but while installing ubuntu 9.10 i gave /home/media as the mount point for my  50 gb hard disk partition
now i cant use it and to do anything in it i need root permissions

now i know how to root login in the terminal
but how to root login in a window is beyond me
please help...

---

### Post by nothingspecial on 2009-12-02
```
sudo chown -R username:username /home/media
```
```

chmod -R 755 /home/media
```

Those might not be the permissions you want, see [[COLOR="Magenta"]here[/COLOR]]("http://linuxcommand.org/lts0070.php")

---

### Post by kellemes on 2009-12-02
[All info about rootpermissions etc.. ]("https://help.ubuntu.com/community/RootSudo")

---

### Post by jbrown96 on 2009-12-02
It would be a better idea to change the permissions, so you don't need root access. There's really two options, depending how you use the drive. 

1) It's used in multiple linux installations. 
2) It's used in one linux installation and/or a windows installtion.

If it's #1, then you probably just want to modify the permissions to let you access the drive without root permissions. 
In a terminal (apps-->accessories) ```
sudo chmod -R o+rw /home/media
```

If it's #2, then it's easier to just change the ownership (and to be safe permissions as well).
```
sudo chown -R $USER:$USER /home/media
``` and ```
sudo chmod -R 666 /home/media
```

---

### Post by bulls_eye on 2009-12-02
i have installed ubuntu 8.10 and 9.10 both on the same machine
so that would fall under the 2nd cadre
right??

---

### Post by abu1237 on 2009-12-02
Please if u know any code of exec() part with using Video codec.
I want to convert all videos to FLV using PHP FFMPEG.
only need execution command.

 						 						 						
					
 					 					 						Here is my code,

<?php
function makeMultipleTwo ($value){
$sType = gettype($value/2);
if($sType == "integer"){
return $value;
} else {
return ($value-1);
}
}

$srcFile = "kabhi-alvida.avi";
$destFile = ".flvs/kabhi-alvida.flv";
$ffmpegPath = "/usr/local/bin/ffmpeg";
$flvtool2Path = "/usr/local/bin/flvtool2";


$ffmpegObj = new ffmpeg_movie($srcFile);


$srcWidth = makeMultipleTwo($ffmpegObj->getFrameWidth());
$srcHeight = makeMultipleTwo($ffmpegObj->getFrameHeight());
$srcFPS = $ffmpegObj->getFrameRate();
$srcAB = intval($ffmpegObj->getAudioBitRate()/1000);
$srcAR = $ffmpegObj->getAudioSampleRate();


$command = $ffmpegPath . " -i " . $srcFile . " -ar " . $srcAR . " -ab " . $srcAB . " -f flv -s " . $srcWidth . "x" . $srcHeight . " " . $destFile . " | " . $flvtool2Path . " -U stdin " . $destFile;
$convert = exec($command);



if(!$convert){
echo "FAILED!!!";
}

?>

What's wrog with this. everything going okey, but output flv file is 0kb. Plz help

---

### Post by bulls_eye on 2009-12-02
one more thing
in your reply you have written

sudo chmod -R 666 /home/media
while nothing special has written

chmod -R 755 /home/media

so what do 666 and 755 imply??

---

### Post by bulls_eye on 2009-12-02
solved

thank you very much

it was the 1st category
thank you very much for making my life easier...

---

### Post by bulls_eye on 2009-12-02
also got the thing about 666 and 755 in the link given by nothingspecial

those are just two different kind of permissions...

---

### Post by jbrown96 on 2009-12-02
There are three types of permissions owner, group, other. The three numbers represent each of those categories. There are three types of permissions for each group (read: 4, write: 2, execute: 1). Whatever permissions you want just add them together. generally you don't want to make something executable unless it's necessary (the GUI takes care of this, so it's never necessary). Therfore, odd number permissions are a security risk. I think that we both meant the same thing, but nothingspecial got the number mixed up. You want read and write permission (4+2=6), and to be safe you give thos permissions to the owner, group, and others -- hence (666).

---

### Post by bulls_eye on 2009-12-04
hmmm

thanks for the enlightenment...

:)

---

