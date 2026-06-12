---
title: "webcam uploader keeps uploading same image"
date: 2010-06-17
forum: General Help
---

### Post by mfearby on 2010-06-17
I'm trying to get the "webcam" program to upload what it sees at regular intervals, and I can get this to work, but the problem is it only uploads the first thing it sees for all eternity. It won't update. Only if I Ctrl+C and run it again will I get a new image uploaded.

Makes no difference if I try "trigger = 1" or "trigger = 0" either. I'm baffled. Any ideas?

Running 10.04 64-bit with a Logitech Webcam that works fine otherwise.

---

### Post by no2498 on 2010-06-17
try this program it has motion, wxcam
read and install all that the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

comes in a deb file also

---

### Post by mfearby on 2010-06-18
> **no2498 said:**
> try this program it has motion, wxcam
read and install all that the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

comes in a deb file also

Thanks for the suggestion. I'll take a look. I did get it working on my Mythbuntu 8.10 box but using an older webcam I had lying around. Must be issues with the newer cam I bought (can't see model number at the moment).

Don't suppose you know of a webcam uploader that will maintain a history of images rather than just replacing the same picture all the time? I keep looking but can't seem to craft the right google search to avoid a flood of useless results.

---

### Post by mfearby on 2010-06-18
After exhausting the possibilities on the 'net I decided to just write what I wanted myself (with a few hand google-code snippets for good measure). Here's what I've done:

The following perl script is called from cron to run the "webcam" command (using settings in my ~/.webcamrc file; most notably with the "once = 1" setting so that it only takes one snapshot) and to upload the image to an FTP site with a unique filename:

```
#!/usr/bin/perl -w

use strict;
use Net::FTP;

my $result = `webcam`;
print $result;

my ($sec,$min,$hour,$mday,$mon,$year,$wday,$yday,$isdst) = localtime(time); 
my $filename = sprintf("webcam-%4d%02d%02d-%02d%02d%02d.jpg", $year+1900,$mon+1,$mday,$hour,$min,$sec);

print "New file to upload: $filename\n";

my $host        = "ftp.site.address.com";
my $dir         = "/";
my $user        = 'username';
my $passwd      = "password";
my $passive     = 1;
my $DEBUG       = 0;

my $ftp = Net::FTP->new($host, Debug => $DEBUG, Passive => $passive) or die "Can't open $host\n";
$ftp->login($user, $passwd) or die "Can't log in as $user\n";
$ftp->cwd($dir) or die "Can't chdir to $dir\n";
$ftp->binary();
$ftp->put('webcam.jpeg', $filename);

$ftp->close();
```

On the web site I wrote the following PHP script to show the most recent images:

```
<html><head><title>Webcam</title>
<style type="text/css">
img { padding: 4px; }
</style>
</head><body>
<?php
header("Expires: Mon, 26 Jul 1997 05:00:00 GMT");
header("Cache-Control: no-cache");
header("Pragma: no-cache");
$files = glob( '*.jpg' );
array_multisort(
  array_map( 'filemtime', $files ),
  SORT_NUMERIC,
  SORT_DESC,
  $files
);
$i = 0;
foreach ($files as $filename) {
	if ($i == 12) break;
	echo '<img src="' . $filename . '" />';
	$i++;
}
?>
</body>
</html>
```

There's also a nice script I found to delete files older than a certain date/time which I'll add to cron soon enough:

[http://www.nervous.it/lang/en-us/2009/08/delete-old-files-from-ftp-server/](http://www.nervous.it/lang/en-us/2009/08/delete-old-files-from-ftp-server/)

Hopefully this might help somebody looking for a nice, simple, solution one day.

---

### Post by no2498 on 2010-06-18
did you try the program, motion it runs in the background
not the 1 in wxcam

---

### Post by mfearby on 2010-06-18
> **no2498 said:**
> did you try the program, motion it runs in the background
not the 1 in wxcam

Um, no... It looked far too complicated for my needs and since I already got "webcam" working, all I needed were a few scripts and hey presto. I already know a bit of perl and PHP so that wasn't hard. A lot quicker than wading through documentation :-)

---

