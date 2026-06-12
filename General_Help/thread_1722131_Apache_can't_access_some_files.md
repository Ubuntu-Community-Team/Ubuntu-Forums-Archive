---
title: "Apache can't access some files"
date: 2011-04-05
forum: General Help
---

### Post by DiNozzo92 on 2011-04-05
Hello!

Have for some time been working on a website in PHP, which has been running in IIS server in Windows 7, but now that I'm going to publish the beta section of the website in Apache Ubuntu, everything goes wrong .. but note that the error only occurs in Apache, not IIS.
IIS7 PHP 5.3.5
Apache2 PHP 5.3.2

Apache website is here:
[Index.php]("http://osterman.dyndns-server.com:81/Diabetic-Journal/Index.php")

And then there's an include, which isn't available:
[NewsSide.php](http://osterman.dyndns-server.com:81/Diabetic-Journal/inc/NewsSide.php)

It's accessable using IIS from Windows but not using Apache from Ubuntu.

NewsSide.php got the following permissions:
```
-rwxr-xr-x 1 root root 1331 2011-03-23 16:30 NewsSide.php
```

NewsSide.php (OBS. *** Is passwords etc..)
```

<?php

/**
 * @author Jonathan Osterman
 * @copyright 2011
 */

    $i = 0;
    
    $news_ID = array(0, 1, 2, 3, 4);
    $news_header = array(0, 1, 2, 3, 4);
    $news_body = array(0, 1, 2, 3, 4);
    $news_date = array(0, 1, 2, 3, 4);
 
    $connect = mysql_connect("osterman.dyndns-server.com:***", "***", "***") or die("Couldn't Connect to Database!");//Database Connection.
    mysql_select_db("***") or die("Couldn't find Database!");//Select of Database.
                    
    $query = mysql_query("SELECT * FROM News");
    $counter = mysql_num_rows($query);
    
    if($counter)
    {
        $query = mysql_query("SELECT * FROM News ORDER BY news_ID DESC");
        
        while($row = mysql_fetch_assoc($query))
        {
            if($i < 5)
            {
                $news_ID[$i] = $row['news_ID'];
                $news_header[$i] = $row['news_Header'];
                $news_body[$i] = $row['news_Short'];
                $news_date[$i] = $row['news_Date'];
                echo("<a href='Index.php?page=News&ID=".$news_ID[$i]."'>
                    <div id='SideBodyHeader'>".$news_date[$i]."</div>
                    <div id='SideBody'>".$news_body[$i]."</div></a>
                    ");
                $i++;
            }
        }
    }

?>

```

phpinfo page:
[php.php](http://osterman.dyndns-server.com:81/php.php)

I would appreciate fast help since I need to launch the beta in about 9 hours.

Regards
Jonathan Osterman

---

