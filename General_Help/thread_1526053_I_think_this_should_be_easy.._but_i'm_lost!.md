---
title: "I think this should be easy.. but i'm lost!"
date: 2010-07-07
forum: General Help
---

### Post by risen75 on 2010-07-07
Ok.. so here's the deal.. I'm trying to do something via command line and i can't seem to figure out where to even start looking.. 

I have a directory with about oh.. 30Gigs of karaoke music and they're all in a crap load of sub-directories.  Now what i want to do is take the names of all of those files, rip out the artist and song name (they are both included in the filename) and add it to a spreadsheet for formating and printing (aka song list books for the drunks at the bars i KJ at)

now I can't see this as being hard.. but I just can't seem to figure out what to look up to write the command....

the files do make it easy though.. in that they're all formated in some variant of the two examples below...

1.  <Disk> - <track> - <artist name> - <song name>.*
2. <artist name> - <song name>.*


Any help would be appreciated as the only way I can think of at the moment would be to do something in the way of this:

ls -R | <spreadsheetprogram> songlist.*

the only problem with that is that it would put them all in one cell and wouldn't do any of the seperation that i'm looking for the computer to do (at that point i might as well do it all manually)  

Thank you all for your continued assistance.. (i'm getting better but still a n00b after all these years)

---

### Post by Yarui on 2010-07-07
If you want something to automatically take all your songs and enter all their information into a spreadsheet, I think you would probably need to write a script to do that for you.  It wouldn't probably be terribly difficult to write, but if you have never written scripts before it may take a bit of research.  It would be a good project to help you break into the world of programming.

---

### Post by risen75 on 2010-07-07
I figured it'd be some sort of script... but where would i start looking? bash scripting?

---

### Post by Yarui on 2010-07-07
I'm not sure if a bash script would be the best way to do that.  If it were me I would probably try to make a python script to do it.  I could be wrong, though, bash may work just fine.

---

### Post by gmargo on 2010-07-07
Here's a quick-n-dirty Perl script that takes a list of filenames, parses them, and prints them in a comma-separated format that you can read into a spreadsheet.

I called this script "parse_music.pl".  Assuming it is in $HOME/bin, run it in your music directory with:
```

find . -type f -print | ~/bin/parse_music.pl > $HOME/music.csv

```The output will look like this:
```

"Willie Nelson","Blue Skies"
"Shakira","Hips Dont Lie"
"Taylor Swift","Beautiful Eyes"

```And here's the Perl script.  It should be simple to add additional filename format options.
```

#!/usr/bin/perl -w
# vim: ts=8 sts=4 sw=4 et :
use strict;
use warnings;
use diagnostics;

#--------------------------------------------------------------------------
# gmargo 2010-07-07
#--------------------------------------------------------------------------
# Parse music file names.
#
# http://ubuntuforums.org/showthread.php?t=1526053
#
# the files do make it easy though.. in that they're all formated
# in some variant of the two examples below...
#
#1. <Disk> - <track> - <artist name> - <song name>.*
#2. <artist name> - <song name>.*
#--------------------------------------------------------------------------

use File::Basename;

# Act as a filter, reading list of newline-terminated filenames
# from standard input.

while (<STDIN>)
{
    #print $_;
    my $line = $_;
    $line =~ s/[[:space:]]+\z//s;

    my $filename = basename $line;

    #1. <Disk> - <track> - <artist name> - <song name>.*
    if ($filename =~ /^
            ([^-]+?)
            \s+-\s+
            (\d+)
            \s+-\s+
            ([^-]+?)
            \s+-\s+
            ([^-.]+?)
            \.(\w+)$/x)
    {
        my ($disk, $track, $artist, $song, $ext) = ($1,$2,$3,$4,$5);
        #print "$line\n";
        #print "disk=\"$disk\"  track=\"$track\"  artist=\"$artist\"  song=\"$song\"  ext=\"$ext\"\n";

        print "\"$artist\",\"$song\"\n";    # Print CSV format.
    }

    #2. <artist name> - <song name>.*
    elsif ($filename =~ /^
            ([^-]+?)
            \s+-\s+
            ([^-.]+?)
            \.(\w+)$/x)
    {
        my ($artist, $song, $ext) = ($1,$2,$3);
        #print "$line\n";
        #print "artist=\"$artist\"  song=\"$song\"  ext=\"$ext\"\n";

        print "\"$artist\",\"$song\"\n";    # Print CSV format.
    }

    else
    {
        print STDERR "Warning: filename \"$filename\" not matched\n";
    }
}

```

---

### Post by risen75 on 2010-07-08
Wow.. I really appreciate you writing a script for me.. :)

Now.. I just have one quick question.... so that i can actually figure out how to modify it so that i don't get all of these 

"Warning: filename "<blank>" not matched 

errors and have it get all of the files.. instead of just oh say the 680 out of almost 10,000 :) 

I'm reading through the script.. and i've got the jist of most of it.. though what i'm having trouble figuring out.. is..

#1. <Disk> - <track> - <artist name> - <song name>.*
    if ($filename =~ /^
            ([^-]+?)
            \s+-\s+
            (\d+)
            \s+-\s+
            ([^-]+?)
            \s+-\s+
            ([^-.]+?)
            \.(\w+)$/x)
    {

ok.. so i get that it's splitting the name up.. but pardon my french.. wtf does the all that mean? (after the if($filename= , i understand that part) 

Thank you for your script and your answer gmargo :) this is a big help

---

### Post by Yarui on 2010-07-08
I don't know much about perl syntax, but this looks like a set of regular expressions to me.  Regular expressions are a form of pattern matching.  I don't really have the patience to trace through it at the moment, but it appears to basically search your home folder for files that match the pattern that has been designated.

Regular expressions tend to look like a large string of random numbers, letters and symbols, so it's understandable that you don't understand those lines.

---

### Post by gmargo on 2010-07-09
Here is another version of the Perl script.  It add two things: 1) documentation for the regular expressions, and 2) an additional filename pattern which I use for mp3s.

```

#!/usr/bin/perl -w
# vim: ts=8 sts=4 sw=4 et :
use strict;
use warnings;
use diagnostics;

#--------------------------------------------------------------------------
# gmargo 2010-07-07 to 2010-07-09
#--------------------------------------------------------------------------
# Parse music file names.
#
# http://ubuntuforums.org/showthread.php?t=1526053
#
# the files do make it easy though.. in that they're all formated
# in some variant of the two examples below...
#
#1. <Disk> - <track> - <artist name> - <song name>.*
#2. <artist name> - <song name>.*
#
# plus add the format I use:
#3. <artist name> - <disk> - <track> - <song name>.*
#--------------------------------------------------------------------------

use File::Basename;

# Act as a filter, reading list of newline-terminated filenames
# from standard input.

while (<STDIN>)
{
    #print $_;
    my $line = $_;
    $line =~ s/[[:space:]]+\z//s;

    my $filename = basename $line;

    #1. <Disk> - <track> - <artist name> - <song name>.*
    if ($filename =~ /
            ^           # beginning of string
            ([^-]+?)    # Non-dash characters, non-greedy (disk name)
            \s+-\s+     # multispace,dash,multispace
            (\d+)       # One or more digits (track number)
            \s+-\s+     # multispace,dash,multispace
            ([^-]+?)    # Non-dash characters, non-greedy (artist name)
            \s+-\s+     # multispace,dash,multispace
            ([^-.]+?)   # Non-dash, non-dot characters, non-greedy (song name)
            \.          # dot
            (\w+)       # alphanumeric chars (file extension)
            $           # end of string
            /x)         # /x says ignore whitespace in regular expresssion,
                        # so that it may be documented like this.
    {
        my ($disk, $track, $artist, $song, $ext) = ($1,$2,$3,$4,$5);
        #print "$line\n";
        #print "disk=\"$disk\"  track=\"$track\"  artist=\"$artist\"  song=\"$song\"  ext=\"$ext\"\n";

        print "\"$artist\",\"$song\"\n";    # Print CSV format.
    }

    #2. <artist name> - <song name>.*
    elsif ($filename =~ /
            ^           # beginning of string
            ([^-]+?)    # Non-dash characters, non-greedy (artist name)
            \s+-\s+     # multispace,dash,multispace
            ([^-.]+?)   # Non-dash, non-dot characters, non-greedy (song name)
            \.          # dot
            (\w+)       # alphanumeric chars (file extension)
            $           # end of string
            /x)         # /x says ignore whitespace in regular expresssion,
                        # so that it may be documented like this.
    {
        my ($artist, $song, $ext) = ($1,$2,$3);
        #print "$line\n";
        #print "artist=\"$artist\"  song=\"$song\"  ext=\"$ext\"\n";

        print "\"$artist\",\"$song\"\n";    # Print CSV format.
    }

    #3. <artist name> - <disk> - <track> - <song name>.*
    elsif ($filename =~ /
            ^           # beginning of string
            ([^-]+?)    # Non-dash characters, non-greedy (artist name)
            \s+-\s+     # multispace,dash,multispace
            ([^-]+?)    # Non-dash characters, non-greedy (disk name)
            \s+-\s+     # multispace,dash,multispace
            (\d+)       # One or more digits (track number)
            \s+-\s+     # multispace,dash,multispace
            ([^-.]+?)   # Non-dash, non-dot characters, non-greedy (song name)
            \.          # dot
            (\w+)       # alphanumeric chars (file extension)
            $           # end of string
            /x)         # /x says ignore whitespace in regular expresssion,
                        # so that it may be documented like this.
    {
        my ($artist, $disk, $track, $song, $ext) = ($1,$2,$3,$4,$5);
        #print "$line\n";
        #print "disk=\"$disk\"  track=\"$track\"  artist=\"$artist\"  song=\"$song\"  ext=\"$ext\"\n";

        print "\"$artist\",\"$song\"\n";    # Print CSV format.
    }

    else
    {
        print STDERR "Warning: filename \"$filename\" not matched\n";
    }
}


```

---

### Post by risen75 on 2010-07-10
thank you for the better docs.. :) now lets see if i can get it working right :)

---

