---
title: "Video script not working?"
date: 2009-10-30
forum: General Help
---

### Post by Bluesplayer on 2009-10-30
Hi

I have a ubuntu server running and want to show videos.  The script is a simple one and doesn't download videos but simply lists youtube videos and then shows the video embedded.  Trouble is the videos are not showing.  You can see what is happening here:

[http://bluesplayer-shops.hopto.org/videos/](http://bluesplayer-shops.hopto.org/videos/)

If you click on a video title you can see the problem.

The script works perfectly here:

[http://bluesplayer.co.uk/videos/](http://bluesplayer.co.uk/videos/)

Obviously I need to install or alter something on my server.  The inside of the index file is this:

```

<?include("config.php");?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" dir="ltr">
    <head profile="http://gmpg.org/xfn/11">
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
        <meta name="keywords" content="<? echo $SEOkeywords ;?>"/>
        <title><? echo $sitename ;?></title>
        <meta name="verify-v1" content="A6pTeEKK3L8B1hU2yZQW5DmIfQJKVq2FB49mQSQ045s=" />
        <link rel="stylesheet" href="/videos/style.css" type="text/css" media="screen" />
    </head>
    <body>

        <div id="container">
            <div id="top">
                <div class="left">
                    <h1 id="site_title"><img src="img/logo.png"></h1>
                    <div id="site_description"><? echo $sitedescription ;?></div>
                </div>
                <span class="right">
                </span>
                <div class="clearer"></div>
            </div>
            <div class="path" id="nav">

                <ul>
                    <li><a href="/videos/">Home</a></li>
                    <li><a href="/videos/cloud.php">Search Cloud</a></li>
                </ul>
                <div class="clearer"></div>
            </div>
            <div id="main">
                <center></center>
                <div class="left" id="main_left">
                    <div id="splash">
                        <div class="container">
                            <div class="post">
                                <div class="body">

                            <?
function trsil($q) { 
$q = str_replace("Ã§","c",$q);
$q = str_replace ("Ã§","c",$q); 
$q = str_replace ("ÄŸ","g",$q); 
$q = str_replace ("Ä°","I",$q); 
$q = str_replace ("Ä±","i",$q); 
$q = str_replace ("ÅŸ","s",$q); 
$q = str_replace ("Ã¶","o",$q); 
$q = str_replace ("Ã¼","u",$q); 
$q = str_replace ("Ãœ","U",$q); 
$q = str_replace ("Ã‡","c",$q); 
$q = str_replace (".","",$q); 
$q = str_replace ("Äž","g",$q); 
$q = str_replace ("Åž","S",$q); 
$q = str_replace ("Ã–","O",$q); 
$q = str_replace (" ","-",$q); 
$q = str_replace ("'","",$q); 
$q = str_replace ("/","",$q); 
$q = str_replace ("--","-",$q); 
 return $q; 
} 

        $data=file_get_contents('http://www.youtube.com/api2_rest?method=youtube.videos.list_by_tag&dev_id=bf22UCJzyh4&tag=KEYWORD-HERE&page=1&per_page=10');
    
        $bol = explode("<video>",$data);
        for ($i=1;$i<=count($bol)-1;$i++) {
        
        preg_match("'<author>(.*?)</author>'si",$bol[$i], $yukleyen);
        preg_match("'<id>(.*?)</id>'si",$bol[$i], $id);
        preg_match("'<title>(.*?)</title>'si",$bol[$i], $adi);
        preg_match("'<description>(.*?)</description>'si",$bol[$i], $aciklama);
        preg_match("'<tags>(.*?)</tags>'si",$bol[$i], $tags);
        preg_match("'<thumbnail_url>(.*?)</thumbnail_url>'si",$bol[$i], $tumb);


?>
                                    <p style="padding:10px; margin-bottom:30px"><a href="/videos/video/<?=$id[1];?>/<?=trsil($adi[1]);?>"><img src="<?=$tumb[1];?>" width="125" height="100" border="0" alt="<?=$adi[1];?>" class="left" /></a><strong><a href="/videos/video/<?=$id[1];?>/<?=trsil($adi[1]);?>"><?=$adi[1];?></a></strong><br />Uploaded by: <a href="/videos/user/<?=$yukleyen[1];?>"><?=$yukleyen[1];?></a><br />
                                        Tags: <?
        $bolx = explode(" ",$tags[1]);
        for ($ix=0;$ix<=count($bolx)-1;$ix++) {
        echo "<a class='tags' href='/videos/tag/$bolx[$ix]'>$bolx[$ix]</a> ";
        }?>
                                    </p><br /><?}?><br /><br />
                                </div>
                                Navigate    <?for ($s=1;$s<=15;$s++) {?><a href=/tag.php?query=pc&page=<?=$s;?>><?=$s;?></a> <?}?>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="right" id="main_right">
                    <div id="sidebar">
                        <h2>Search</h2>
                        <div class="content">
                            <form method="get" id="searchform" action="/videos/tag.php">
                                <div>
                                    <input type="text" value="" name="query" id="query" class="searchbox"/>
                                    <input type="submit" id="searchsubmit" value="Search" class="submit" />
                                </div>
                            </form>
                        </div>
                        <h2>Links</h2>
                        <ul class="content">
                            <li><a href="http://www.themeforest.net" target="_blank">Theme Forest</a></li>
                            <li><a href="http://www.hostgator.com" target="_blank">Host Gator</a></li>
                            <li><a href="http://www.junglescripts.com" target="_blank">Jungle Scripts</a></li>
                        </ul>
                        <center>
                            <div class="advert_banner"><a href="http://themeforest.net/user/junglescripts?ref=junglescripts"><img src="http://themeforest.net/new/images/ms_referral_banners/TF_120x600.jpg"></a>
                            </div>
                        </center>
                    </div>
                </div>
                <div class="clearer"></div>
            </div>
            <div id="footer">
                <div class="left">
                    &copy; 2008 <a href="#"><? echo $siteurl ;?></a> | <a href="#top">Go to top</a>
                </div>
                <div class="right">Site Developed by <a href="http://junglescripts.com">Jungle Scripts</a>
                </div>
                <div class="clearer"></div>
            </div>
        </div>
    </body>
</html>

```Any idea what I need to do to make this script work?

Regards
Bluesplayer

---

