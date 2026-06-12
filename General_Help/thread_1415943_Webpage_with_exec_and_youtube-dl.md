---
title: "Webpage with exec and youtube-dl"
date: 2010-02-25
forum: General Help
---

### Post by Kemon on 2010-02-25
I have made a youtube downloading script you my server/desktop that download the flw file and convert it to mp3, I want to make a php script that download and convert it so I can download just the mp3-file.

youtube.sh with user:www-data and 755 access:
```
#! /etc/bach
if [ "$1" ]; then

        cd "/var/www/youtube/mp3"
        youtube-dl $1
        ffmpeg -i "$1.flv" -ab 128k "$1.mp3"
        mv "$1.mp3" "$2.mp3"
        rm "$1.flv"
fi
```

/var/www/youtube/index.php:
[PHP]<?

$dl = $_POST['dl'];
$new_name = $_POST['new_name'];
if($dl && $new_name){
if(exec("sh ./yt.sh $dl '$new_name'", $out)) {
        echo "<a href='http://WEBADDRESS.com/youtube/mp3/$new_name.mp3'>[RightClick, save as]</a>";
        print_r($out);
}
}
?>
<form method="post" action="">
Youtube link: <input type="text" name="dl"><br>
Nytt navn: <input type="text" name="new_name"><br>
<input type="submit" value="Convert and download">
</form>
[/PHP]
My problem is that the script is not "loading" long enugh to download and convert the file so I made a output var $out that says:
```
Array ( [0] => Retrieving video webpage... done. [1] => Extracting URL "t" parameter... done. [2] => Requesting video file... done. [3] => Video data found at http://v16.lscache2.c.youtube.com/videoplayback?ip=0.0.0.0&sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Calgorithm%2Cburst%2Cfactor&fexp=905210%2C900022%2C904704%2C906103&algorithm=throttle-factor&itag=5&ipbits=0&burst=40&sver=3&expire=1267146000&key=yt1&signature=834FB7D42000C8CA343C9905197E95AF477CEF0A.22DAEAB6E74D6B330D634F55BDA50CF511A4E22A&factor=1.25&id=d999a4b16c9a7090 )
```

It works in shell/putty but not on the webpage..
Any ide?

Thanks

---

