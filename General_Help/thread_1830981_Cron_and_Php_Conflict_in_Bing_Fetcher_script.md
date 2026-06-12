---
title: "Cron and Php Conflict in Bing Fetcher script?"
date: 2011-08-22
forum: General Help
---

### Post by passonno on 2011-08-22
I recently followed instructions from [here]("http://bit.ly/18EPcW") to enable fetching Bing wallpapers from the web.  It does work manually,  however,  when I try it with cron,  I get the following:

>  PHP Warning:  file_get_contents(bing): failed to open stream: No such file or directory in /home/anthony/bing.php on line 28
rm: cannot remove `bing': No such file or directory
PHP Notice:  Undefined offset: 1 in /home/anthony/bing.php on line 31
PHP Notice:  Undefined offset: 1 in /home/anthony/bing.php on line 32
Press ENTER to continue and close this window.

Here are the pertinent lines from the php script:  [PHP]$dump = file_get_contents("bing");
system("rm bing");
$chunks = explode("g_img=", $dump);
$temps = explode("'", $chunks[1]);
$url = "http://www.bing.com/".$temps[1];
[/PHP]

---

### Post by gsgleason on 2011-08-22
The first command is failing.  Since you're not specifying the full path to 'bing' I am guessing it's using the same directory as the script.

Try specifying the full path to the file 'bing' in the first line.

---

### Post by passonno on 2011-08-22
Well,  as far as I can tell,  there is no file simply named "bing" in the directory.  I will try by creating an empty file called "bing" and report results.

---

### Post by passonno on 2011-08-22
Well,  aside from the "undefined offset" errors,  it worked when I created the empty file.  Then it removed it,  which it is supposed to do.  It isn't a problem running it manually,   but I wonder if I added "touch bing" before that first command if it would blow up or actually work?

---

### Post by passonno on 2011-08-22
So far so good,  and I just learned a little PHP!!!  I inserted the system command to create the empty file,  and it worked.  That said,  I wonder if I can depend on that to work when the next wallpaper comes out?  Still no ideas about those other errors,  but it does what I want it to,  so far.


Thanks for your help.

---

### Post by gsgleason on 2011-08-22
I just looked at the link you provided, and it looks like what you posted is incomplete.  The first thing the script does is download the html for [http://www.bing.com](http://www.bing.com) to a file called 'bing' which you have left out.

---

### Post by passonno on 2011-08-22
You know,  I was beginning to wonder why my home directory was filling up with index.html files.  Interesting.

---

### Post by gsgleason on 2011-08-22
Also, with php, instead of calling wget to download the bing page to a file, loading the file to a string, then removing the file, you can just use file_get_contents to open the url directly.

---

### Post by passonno on 2011-08-22
Having tried that approach,  I have hit a brick wall,  due to my limited understanding of how PHP works,  and the function itself.  Is there a switch available,  similar to the wget command,  that I am missing?

---

### Post by gsgleason on 2011-08-22
try this:

Replace these lines:

[PHP]system("wget -q http://www.bing.com -O bing");
$dump = file_get_contents("bing");
system("rm bing");[/PHP]

With this line:

[PHP]$dump = file_get_contents("http://www.bing.com");[/PHP]

---

### Post by passonno on 2011-08-22
Perfect.  I just learned a bit more about PHP in the process.  Thank you very much.

---

### Post by passonno on 2011-08-22
Now,  to make it happen silently,  with no terminal output.  Working on that now.  Thanks a bunch for your help.

---

