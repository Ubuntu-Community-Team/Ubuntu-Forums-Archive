---
title: "Cron Help Please."
date: 2009-10-29
forum: General Help
---

### Post by CosmicSea on 2009-10-29
I dont know why my script wont run. I have tried several solutions and im thinking maybe its the script? I know cron is working cause i used a script to make a new text document every minute and that worked and i dont know what to do. i need some help. 
im trying to get it to run every hour but first i need to get it going. is there a way i can execute the php file myself to make sure it works? i use ubuntu 8.04.

here is my cron code

*/60 * * * * /home/public_html/domain.com/public/username/cron/parser.php



and here is the file im trying to run. do you see anything wrong?





[html]#!/usr/bin/php
<?php
include "./../functions.php";
include "./../config.php";
chdir("/home/public_html/domain.com/public/username/cron/");
if(file_exists("run-p.flag"))
{
    exec("rm run-p.flag");
    sleep(1);
    if(file_exists("run-p.flag")) exit("can't clean run-p.flag");
    sleep(60);
}
exec("rm log-p.txt");
touch("run-p.flag");
if(mt_rand(1,300)==27)
{
    include "./tagcloud.php";
    exec("rm run-p.flag");
    logstr("log-p.txt","[end]".date("Y-m-d H:i:s")."[/end] \n");
    exit();
}


set_time_limit(1000);
ignore_user_abort(true);
logstr("log-p.txt","[start]".date("Y-m-d H:i:s")."[/start] \n");
print "<pre>\n";

$query=mysql_query("SELECT `id`,`keyword` FROM `v2keywords` ORDER BY `lastcheck`,RAND() LIMIT 4");
while($row=mysql_fetch_row($query))
{
    get_urls_by_kwd("\"rapidshare.com/files\" ".$row[1],"/rapidshare\.com\/files\/(\d+)\/([^\'^\"^\s^>^<^\\^\/]+)/",1);
    get_urls_by_kwd("\"badongo.com/file\" ".$row[1],"/badongo\.com\/file\/(\d+)/",2);
    get_urls_by_kwd("\"mediafire.com/?\" ".$row[1],"/mediafire\.com\/\?(\w+)/",3);
    get_urls_by_kwd("\"sendspace.com/file\" ".$row[1],"/sendspace\.com\/file\/(\w+)/",4);
    get_urls_by_kwd("\"4shared.com/file\" ".$row[1],"/4shared\.com\/file\/(\d+)\/(\w+)\/([^\'^\"^\s^>^<^\\^\/]+)/",5);
    
    mysql_query("UPDATE `v2keywords` SET `lastcheck`=NOW() WHERE `id`='".$row[0]."'");
    if(mysql_errno()) print mysql_error()."\n";
}
print "</pre>";
exec("rm run-p.flag");
logstr("log-p.txt","[end]".date("Y-m-d H:i:s")."[/end] \n");
?>[/html]

---

### Post by mobilediesel on 2009-10-29
> **CosmicSea said:**
> I dont know why my script wont run. I have tried several solutions and im thinking maybe its the script? I know cron is working cause i used a script to make a new text document every minute and that worked and i dont know what to do. i need some help. 
im trying to get it to run every hour but first i need to get it going. is there a way i can execute the php file myself to make sure it works? i use ubuntu 8.04.

here is my cron code

*/60 * * * * /home/public_html/domain.com/public/username/cron/parser.php



and here is the file im trying to run. do you see anything wrong?





[html]#!/usr/bin/php
<?php
include "./../functions.php";
include "./../config.php";
chdir("/home/public_html/domain.com/public/username/cron/");
if(file_exists("run-p.flag"))
{
    exec("rm run-p.flag");
    sleep(1);
    if(file_exists("run-p.flag")) exit("can't clean run-p.flag");
    sleep(60);
}
exec("rm log-p.txt");
touch("run-p.flag");
if(mt_rand(1,300)==27)
{
    include "./tagcloud.php";
    exec("rm run-p.flag");
    logstr("log-p.txt","[end]".date("Y-m-d H:i:s")."[/end] \n");
    exit();
}


set_time_limit(1000);
ignore_user_abort(true);
logstr("log-p.txt","[start]".date("Y-m-d H:i:s")."[/start] \n");
print "<pre>\n";

$query=mysql_query("SELECT `id`,`keyword` FROM `v2keywords` ORDER BY `lastcheck`,RAND() LIMIT 4");
while($row=mysql_fetch_row($query))
{
    get_urls_by_kwd("\"rapidshare.com/files\" ".$row[1],"/rapidshare\.com\/files\/(\d+)\/([^\'^\"^\s^>^<^\\^\/]+)/",1);
    get_urls_by_kwd("\"badongo.com/file\" ".$row[1],"/badongo\.com\/file\/(\d+)/",2);
    get_urls_by_kwd("\"mediafire.com/?\" ".$row[1],"/mediafire\.com\/\?(\w+)/",3);
    get_urls_by_kwd("\"sendspace.com/file\" ".$row[1],"/sendspace\.com\/file\/(\w+)/",4);
    get_urls_by_kwd("\"4shared.com/file\" ".$row[1],"/4shared\.com\/file\/(\d+)\/(\w+)\/([^\'^\"^\s^>^<^\\^\/]+)/",5);
    
    mysql_query("UPDATE `v2keywords` SET `lastcheck`=NOW() WHERE `id`='".$row[0]."'");
    if(mysql_errno()) print mysql_error()."\n";
}
print "</pre>";
exec("rm run-p.flag");
logstr("log-p.txt","[end]".date("Y-m-d H:i:s")."[/end] \n");
?>[/html]

the code for the cron should be:
```
0 * * * * /home/public_html/domain.com/public/username/cron/parser.php
```

and as for the php, I don't know much about php programming but you can make sure the file is executable with this:
```
chmod +x parser.php
```
Then you can just run it from the command line to test.

---

### Post by CosmicSea on 2009-10-29
ok i tried the command to run the file and it works. thank you for that! now i just need to get the cron working. any ideas why it wont work? i want to make a code to test it before i try to run it cause it just wont run from what i have seen and tried.

---

### Post by mobilediesel on 2009-10-29
> **CosmicSea said:**
> ok i tried the command to run the file and it works. thank you for that! now i just need to get the cron working. any ideas why it wont work? i want to make a code to test it before i try to run it cause it just wont run from what i have seen and tried.

Is the public_html directory right under the home directory or under /home**/user**/public_html/ ?
Where **user** is your username?

---

### Post by CosmicSea on 2009-10-29
> **mobilediesel said:**
> Is the public_html directory right under the home directory or under /home**/user**/public_html/ ?
Where **user** is your username?

this is how it looks

/home/public_html/mydomain.com/public/SubDomain/

---

### Post by CosmicSea on 2009-10-29
i have 2 directories 
was i suppost to put public_html in under my username and so on?

/home/username/ with some junk files in it and thats it
/home/public_html

---

### Post by mobilediesel on 2009-10-29
> **CosmicSea said:**
> this is how it looks

/home/public_html/mydomain.com/public/SubDomain/

Cron can use a different shell environment when it runs compared to running in a terminal. The php script doesn't look like it depends on the specific environment, though.

```
0 * * * * /home/public_html/mydomain.com/public/SubDomain/parser.php
```

Should do it but maybe someone who knows php better than I do can see if I missed something.

---

### Post by CosmicSea on 2009-10-29
what does this do? my script has been working ever since i did that. does that run the script constantly or what? it has a running time of 1000 secs i believe and i want to make sure it isnt running constantly for some reason. also does the 0 * * * * make it run every hour? thanks for helping me!
chmod +x parser.php

---

### Post by CosmicSea on 2009-10-29
i meant what does this do 
chmod +x parser.php

---

### Post by mobilediesel on 2009-10-29
> **CosmicSea said:**
> what does this do? my script has been working ever since i did that. does that run the script constantly or what? it has a running time of 1000 secs i believe and i want to make sure it isnt running constantly for some reason. also does the 0 * * * * make it run every hour? thanks for helping me!
chmod +x parser.php

chmod +x parser.php sets the executable bit so the operating system knows it's a program. That only needs to be done once.
0 * * * * runs it every hour, every time the minutes show as 0. You could also make it 25 * * * * so it runs at 25 minutes past every hour.

I have my public_html under my username but you could really put it anywhere as long as you tell your webserver where it is.

---

### Post by CosmicSea on 2009-10-29
nevermind lol.. 1000 secs wouldnt even be done yet so the script should stop when its done. god im tired.

---

### Post by CosmicSea on 2009-10-29
> **mobilediesel said:**
> chmod +x parser.php sets the executable bit so the operating system knows it's a program. That only needs to be done once.
0 * * * * runs it every hour, every time the minutes show as 0. You could also make it 25 * * * * so it runs at 25 minutes past every hour.

I have my public_html under my username but you could really put it anywhere as long as you tell your webserver where it is.
ok cool, sounds good. hopefully it will work. i will find out on the hour.

---

### Post by mobilediesel on 2009-10-29
> **CosmicSea said:**
> ok cool, sounds good. hopefully it will work. i will find out on the hour.

Cron isn't the most user-friendly thing to set up. Once you get it, though, it's literally "set it and forget it."

---

### Post by CosmicSea on 2009-10-29
as far as i can tell it my script is runnig fine. thanks alot!

---

### Post by CosmicSea on 2009-10-29
oh yeah, also, is there any way to make lets say 5 files run one after another 24/7? what i mean is lets say file 1 runs first hour, file 2 runs second hour, file 3 runs third hour, file 4 runs fourth hour, file 5 runs 5th hour, file 1 runs 6th hour, and so on like that repeating itself?  if so what would the * * * * * codes be?

---

### Post by mobilediesel on 2009-10-29
> **CosmicSea said:**
> as far as i can tell it my script is runnig fine. thanks alot!

Glad I could help! Cron was tricky for me when I first tried messing with it. Now it's almost like a second language even though I don't have to do much with it.

In cron, instead of the "* * * * *", you can also use:
```
string	   meaning
------	   -------
@reboot	   Run once, at startup.
@yearly	   Run once a year, same as "0 0 1 1 *"
@annually	   (sames as @yearly)
@monthly	   Run once a month, same as "0 0 1 * *"
@weekly	   Run once a week, same as "0 0 * * 0"
@daily	   Run once a day, same as "0 0 * * *"
@midnight	   (same as @daily)
@hourly	   Run once an hour, same as "0 * * * *"
```

---

### Post by CosmicSea on 2009-10-31
turns out my script is not running. when i did the chmod +x parser.php command my script ran and then hasnt ran ever since. i rebooted and tried that command again to see if the script would run and it wont so im still stuck. anyone have any suggestions for me or anything?

---

### Post by CosmicSea on 2009-10-31
i have this instruction with the script for cron 
/usr/bin/php  /home/yourusername/public_html/domain.com/cron/parser.php

why would there be the /usr/bin/php in the beginning? i tried using that with both directories i have. the "/home/public_html/domain.com/" and
"/home/username/" but no go.

---

### Post by mobilediesel on 2009-10-31
> **CosmicSea said:**
> i have this instruction with the script for cron 
/usr/bin/php  /home/yourusername/public_html/domain.com/cron/parser.php

why would there be the /usr/bin/php in the beginning? i tried using that with both directories i have. the "/home/public_html/domain.com/" and
"/home/username/" but no go.

The /usr/bin/php shouldn't have to be there if the execute bit is set on the file itself. That's what the chmod +x did.

Maybe try copy and paste the file's path to make sure it's right.

---

### Post by CosmicSea on 2009-10-31
[quote=mobilediesel;8203822]The /usr/bin/php shouldn't have to be there if the execute bit is set on the file itself. That's what the chmod +x did.

I just tried that and it didnt seem to work. I did notice that my sub directory under public had a capitol and i made it capitol in cron. i dont know what to do anymore this is very frusterating, its like it will never work lol. is there any way to test to see if the script is running or would an error give me an error if something was wrong? i test it like this right now. lets say it is 3:22 am like it is where i am so to test it, in crontab -e i put 22 3 * * * /directories 
would that be corrert for that time? of course i dont set it to 3:22 at 3:22 i set it there at 3:20 and execute and wait.

---

### Post by mobilediesel on 2009-10-31
> **CosmicSea said:**
> I just tried that and it didnt seem to work. I did notice that my sub directory under public had a capitol and i made it capitol in cron. i dont know what to do anymore this is very frusterating, its like it will never work lol. is there any way to test to see if the script is running or would an error give me an error if something was wrong? i test it like this right now. lets say it is 3:22 am like it is where i am so to test it, in crontab -e i put 22 3 * * * /directories 
would that be corrert for that time? of course i dont set it to 3:22 at 3:22 i set it there at 3:20 and execute and wait.

Yes, the filesystem is case-sensitive. That trips up most of us when using Unix-like operating systems for the first time.

Yes, **22 3 * * *** would be 3:22am.
After the time when the script should run, in a terminal enter:
```
grep CRON /var/log/syslog
```
and it will show you the log entries made by the cron system. It should show you when it runs or an error if it couldn't run for some reason.

---

### Post by CosmicSea on 2009-10-31
ok i ran it and checked the logs and it seems it has been running every hour in the log, but the script doesnt seem to do anything. i dont see why it wont work.

---

### Post by mobilediesel on 2009-10-31
> **CosmicSea said:**
> ok i ran it and checked the logs and it seems it has been running every hour in the log, but the script doesnt seem to do anything. i dont see why it wont work.

From looking at the script as you posted earlier I can't tell why it's not doing anything. Now we'll have to see if someone who knows php can help out. I'm just barely learning php myself so can't really tell you anything about it.

See if you can change the thread title to ask for php help since cron seems to be doing its thing.

---

### Post by CosmicSea on 2009-10-31
> **mobilediesel said:**
> From looking at the script as you posted earlier I can't tell why it's not doing anything. Now we'll have to see if someone who knows php can help out. I'm just barely learning php myself so can't really tell you anything about it.

See if you can change the thread title to ask for php help since cron seems to be doing its thing.

ok i will do that but first im just going to see if i can get it going myself today and if not i will rename the thread. thanks for all your help though i really appreciate it!

---

### Post by CosmicSea on 2009-10-31
i dont think its my file. if i run the command php parser.php it runs smooth with no errors. so it has to be cron but cron doesnt show any errors that i can see so i have no clue what to do.

---

### Post by mobilediesel on 2009-11-01
> **CosmicSea said:**
> i dont think its my file. if i run the command php parser.php it runs smooth with no errors. so it has to be cron but cron doesnt show any errors that i can see so i have no clue what to do.

Maybe this link can help: [http://www.htmlcenter.com/blog/running-php-scripts-with-cron/](http://www.htmlcenter.com/blog/running-php-scripts-with-cron/)
They show the cron entry with * * * * * which would run every minute. You'd still want it as 0 * * * *

---

