---
title: "Another Crontab Issue"
date: 2012-03-28
forum: General Help
---

### Post by superdaveozzborn on 2012-03-28
i downloaded this script from here [http://wiki.gotux.net/code/perl/atget ]("http://wiki.gotux.net/code/perl/atget")
it will download all the current trailers from apple.com and place them in a folder called trailers.


after playing around with it i did edit it a little to use full path to the files. 
example, was "trailers.xml" changed to "/media/Archive01/Data/trailers.xml" and so on.

```
#!/usr/bin/perl
## ATGet v0.1 - Apple Trailers Downloader
## Coded by TuxLyn {2012-03-14}

use XML::Simple;

if ($ARGV[0] eq '-d') { &download(); } else { &usage(); }

sub usage {
print "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ATGet v0.1, apple trailers downloader
Coded by TuxLyn (http://gotux.net/)
Usage: $0 [option] [input] [output]
  -d    download latest apple trailers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
";
} #usage

sub download {
  mkdir '/media/Archive01/Data/trailers';
  unlink '/media/Archive01/Data/trailers.xml';
  system('wget "http://trailers.apple.com/trailers/home/xml/current.xml" -O /media/Archive01/Data/trailers.xml');
  $xml = new XML::Simple;
  $data = $xml->XMLin('/media/Archive01/Data/trailers.xml', ForceArray => 1, KeyAttr => {});
  foreach my $movie (@{$data->{movieinfo}}) {
    foreach my $trailer (@{$movie->{info}}) {
      @titles = ($trailer->{title}->[VALUE]);
      @dates = ($trailer->{releasedate}->[VALUE]);
    } #trailer
    foreach my $trailer (@{$movie->{preview}}) {
      foreach my $file (@{$trailer->{large}}) {
        @links = ($file->{content});
      } #file
    } #trailer
    $titles[0] =~ s/The\s//g;
    $titles[0] =~ s/[^a-z A-Z 0-9]*//g;
    $titles[0] =~ s/\s/./g;
    system("wget -U QuickTime/7.6.9 $links[0] -O \"trailers/$titles[0]_$dates[0].mov\"");
  } #movie
} #download

## EOF: atget.pl
```if i open nautilus and navigate to the perl script location /media/Archive01/Data and open terminal there all i need is to enter "./atget.pl -d" and away it goes. every thing works fine as planned. works perfectly.

so i decided to set it up as a cron job. (not my first cron job)
0 15 * * 3 /usr/bin/perl /media/Archive01/Data/atget.pl -d >> /media/Archive01/Data/mycron.log 2>&1

for some reason the script will not rename the current.xml file that i downloads to trailer.xml also there is no trailers.xml file in /media/Archive01/Data where it is supose to be, however if i look in my home folder i find current.xml there. but the script is looking for it in /media/Archive01/Data. so i get an error that file not found and line number where error happened in the atget.pl script. line 24.

it seams to me that this is a permissions issue however i have no idea how to correct this. 

i also have a log file which is created by crontab

```
--2012-03-28 17:50:53--  http://trailers.apple.com/trailers/home/xml/current.xml
Resolving trailers.apple.com... 184.51.156.57, 184.51.156.41
Connecting to trailers.apple.com|184.51.156.57|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 211136 (206K) [application/xml]
Saving to: `current.xml'

     0K .......... .......... .......... .......... .......... 24% 85.0K 2s
    50K .......... .......... .......... .......... .......... 48%  152K 1s
   100K .......... .......... .......... .......... .......... 72% 99.3K 1s
   150K .......... .......... .......... .......... .......... 96%  108K 0s
   200K ......                                                100% 45.1K=2.0s

2012-03-28 17:50:56 (102 KB/s) - `current.xml' saved [211136/211136]

--2012-03-28 17:50:56--  http://-o/
Resolving -o... failed: Name or service not known.
wget: unable to resolve host address `-o'
/media/Archive01/Data/trailers.xml: Scheme missing.
FINISHED --2012-03-28 17:50:58--
Downloaded: 1 files, 206K in 2.0s (102 KB/s)
File does not exist: /media/Archive01/Data/trailers.xml at /media/Archive01/Data/atget.pl line 24
```really scratching my head over this one. probably over thinking it.
any one have any ideas?????

---

### Post by superdaveozzborn on 2012-03-28
here is log file when running from terminal

command used is 

./atget.pl -d >> mycron.log 2>&1

output is file called mycron.log 

```

--2012-03-28 18:09:17--  http://trailers.apple.com/trailers/home/xml/current.xml
Resolving trailers.apple.com... 184.51.156.43, 184.51.156.41
Connecting to trailers.apple.com|184.51.156.43|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 211136 (206K) [application/xml]
Saving to: `/media/Archive01/Data/trailers.xml'

     0K .......... .......... .......... .......... .......... 24%  368K 0s
    50K .......... .......... .......... .......... .......... 48%  343K 0s
   100K .......... .......... .......... .......... .......... 72%  352K 0s
   150K .......... .......... .......... .......... .......... 96%  313K 0s
   200K ......                                                100% 11802G=0.6s

2012-03-28 18:09:17 (353 KB/s) - `/media/Archive01/Data/trailers.xml' saved [211136/211136]

--2012-03-28 18:09:18--  http://trailers.apple.com/movies/sony_pictures/21jumpstreet/21jumpstreet-tlr1_h640w.mov
Resolving trailers.apple.com... 184.51.156.43, 184.51.156.41
Connecting to trailers.apple.com|184.51.156.43|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24472155 (23M) [video/quicktime]
Saving to: `trailers/21.Jump.Street_2012-03-16.mov'

     0K .......... .......... .......... .......... ..........  0%  415K 57s
    50K .......... .......... .......... .......... ..........  0%  341K 64s

sniped out middle

20550K ........                                              100% 37.5M=59s

```

then moves  on to the next download. works grate.

---

### Post by jim_deadlock on 2012-03-28
You shouldn't need to invoke perl because it's already called at the top of the script, so try this instead:

```

0 15 * * 3 /media/Archive01/Data/atget.pl -d >> /media/Archive01/Data/mycron.log 2>&1
```

---

### Post by superdaveozzborn on 2012-04-10
well i still have no luck with this working correctly as a cronjob.

i have even contacted the creator of the script and no luck. this has to be something to do with cron and the way ubuntu uses it. so this thred is closed. thank you for your reply jim_deadlock ):P

---

### Post by jim_deadlock on 2012-04-10
I've tweaked the script for you below, just change the $myfolder variable at the top and it should now work as a cron job.

EDIT: It's probably not such a good idea to use /media because you normally need root permissions, just do it all in your home folder somewhere.

```
#!/usr/bin/perl
## ATGet v0.1 - Apple Trailers Downloader
## Coded by TuxLyn {2012-03-14}

$myfolder = '/home/jim/appletrailers';

use XML::Simple;

if ($ARGV[0] eq '-d') { &download(); } else { &usage(); }

sub usage {
print "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ATGet v0.1, apple trailers downloader
Coded by TuxLyn (http://gotux.net/)
Usage: $0 [option] [input] [output]
  -d    download latest apple trailers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
";
} #usage

sub download {
  chdir ("$myfolder");
  foreach ('Data','Data/trailers') { mkdir ("$_"); }
  chdir ('Data');
  unlink ('trailers.xml');
  system("wget \"http://trailers.apple.com/trailers/home/xml/current.xml\" -O $myfolder/Data/trailers.xml");
  $xml = new XML::Simple;
  $data = $xml->XMLin("$myfolder/Data/trailers.xml", ForceArray => 1, KeyAttr => {});
  foreach my $movie (@{$data->{movieinfo}}) {
    foreach my $trailer (@{$movie->{info}}) {
      @titles = ($trailer->{title}->[VALUE]);
      @dates = ($trailer->{releasedate}->[VALUE]);
    } #trailer
    foreach my $trailer (@{$movie->{preview}}) {
      foreach my $file (@{$trailer->{large}}) {
        @links = ($file->{content});
      } #file
    } #trailer
    $titles[0] =~ s/The\s//g;
    $titles[0] =~ s/[^a-z A-Z 0-9]*//g;
    $titles[0] =~ s/\s/./g;
    system("wget -U QuickTime/7.6.9 $links[0] -O \"trailers/$titles[0]_$dates[0].mov\"");
  } #movie
} #download

## EOF: atget.pl
```

---

### Post by superdaveozzborn on 2012-05-02
thank you for the help.

---

### Post by TuxLyn on 2012-06-04
I've coded version 0.2 if any interested its on my wiki at [http://wiki.gotux.net/code/perl/atget](http://wiki.gotux.net/code/perl/atget)

---

