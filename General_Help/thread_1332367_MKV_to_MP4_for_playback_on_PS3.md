---
title: "MKV to MP4 for playback on PS3"
date: 2009-11-20
forum: General Help
---

### Post by squiggie on 2009-11-20
Hello all. I've been running into a brick wall on this for a couple weeks so I thought I'd post and let the experts help me. I have some SD and HD mkv files that I'm trying to get to play on my ps3 via mediatomb. I couldn't ever get transcoding to work with mediatomb, so I thought I'd just go ahead and take the time to either convert them or remux them into mp4. Nothing I've done seems to work and I'll explain in detail.

First, I followed this guide [http://ubuntuforums.org/showthread.php?t=548547]("http://ubuntuforums.org/showthread.php?t=548547") detailing how to demux the mkv to get the audio and video seperate, convert the audio to aac (because mp4 only takes aac audio) and then remux them with MP4Box to get a h264 mp4. I have tried that at least 3 times on a HD mkv and it has not worked. When I try to stream it to the ps3, it will either give me a Data is corrupt error or something about the file type not supported. Most often it is the data is corrupt error. From that tutorial I specifically followed hansa56 first post so I didn't have to reencode the video.

When that didn't work, and I failed at that a few times, I decided to forgot about it and just reencode the video to xvid. I used mencoder to encode the mkv with this command.

```
mencoder input.mkv -o /dev/null -ovc xvid -xvidencopts bitrate=3000:pass=1 -oac libfaac -ac 2 -ab 128k
```

```
mencoder input.mkv -o output.avi -ovc xvid -xvidencopts bitrate=3000:pass=2 -oac libfaac -ac 2 -ab 128k
```

After several hours of encoding, I got the resulting xvid avi which is playable on a PC, but then I try to stream it to the ps3, I get the Data Corrupt error. What am I doing wrong? I can play tons of other divx and xvid avi files with no problem. Is there something about the HD file? it is 1280x720 resolution. 

If anyone has got mkv to mp4 or any other format that is working on the ps3 please let me know how. I'm not opposed to using Windows utilities, but obviously I'd prefer to stick with the command line on my ubuntu server.

---

### Post by KhaaL on 2009-11-21
hey, just wanted to say i'm in the same boat more or less. I've found a temporarly solution with PlaystationMediaServer:  [http://ps3mediaserver.blogspot.com/](http://ps3mediaserver.blogspot.com/)
I found PMS to be much easier to start and work with than mediatomb. However, since they remux (?) on the fly you can't use the fastforward function. It can also get a bit flaky at times and 1080p movies can lag real bad (at least if you want subtitles).

I don't think you need to re-encode the movies, just re-encapsulate them... once I find a solution I'll post it here...

---

### Post by Emanuele_Z on 2009-12-06
Hi guys,

after some searching around I found out a script in a post of 2008 (now locked).
That script needed some mkv... tools, MP4Box and neroAacEnc (closed source but free). It had a constraint to produce video files whose sizes (x and y) had to be divisible by 16; luckily the newer PS3 OS will support all the sizes.
Then I didn't like to use closed source binary neroAacEnc, so I replaced the command line with the equivalent faac.
Naturally the script won't touch the video stream (no re-encoding): will only convert the audio stream to AAC.

To run the script you'll need the following:
```
sudo apt-get install mkvtoolnix gpac faac ffmpeg
```

Following is the script:
```

#!/usr/bin/perl
#######################################################################
#
#  File:        mkv2mp4.pl
#  Author(s):   Justin Randall (randall311 AT yahoo DOT com)
#               Josh Carroll   (josh.carroll AT gmail DOT com)
#  Version:     0.1
#  Created:     29 April 2008
#  Last Change: Wed May 14 10:00 PM 2008 EDT
#  Description: This script takes an MKV file as input and produces
#               a MP4 (h264/aac) which will play back on the
#               Sony PlayStation 3 (tm)
#  Usage:       mkv2mp4.pl <maktrosa input file>
#  History:     none
#
#  Copyright (c) 2008 by Josh Carroll (josh.carroll AT gmail DOT com)
#  under the name mkv4ps3.  This is a highly modified version used to
#  produce an MP4 (h264/aac) from a mkv file in an automated fashion
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
#  GNU General Public License for more details.
#
#######################################################################
use warnings;
use strict;
use Getopt::Long;
use POSIX qw(floor);
use Cwd qw(realpath);
use File::Basename;

my $prog = $0;
$prog =~ s/.*\///img;

if ($#ARGV != 0) {
   print "Usage: $prog <maktrosa input file>\n";
   exit 0;
}

# set the input based off the command arguments
my $opt_in = $ARGV[0];

my($name, $path, $suffix) = fileparse($opt_in, qr{\..*});

if ($suffix eq '') {
   print "input file did not contain a suffix!\n";
   exit -1;
}

# remove file extension from input file
my $char = 0;
my $basename = $opt_in;
while ($char ne '.') {
   $char = chop $basename;
}

# temoprary files and variables
my $opt_tmp = $basename;
$opt_tmp = "$opt_tmp";
my $opt_out = "$basename.mp4";
my $tmp_ac3 = "$name.ac3";
my $tmp_dts = "$name.dts";
my $tmp_h264 = "$name.h264";
my $tmp_wav_fifo = "$name.wav";
my $tmp_aac = "$name.aac";
my $tmp_mp4 = "t.$name.mp4";

# make sure we have all the tools
check_required_tools();

# make sure the mkv file is correct format
tprint("Checking input file format...\n");
check_resolution($opt_in);

tprint("Extracting mkv file...\n");
# get the fps of the video and the duration (in seconds) of the MKV, and
#	extract the mkv (if only re-muxing to mp4 with aac)
my ($vid_fps,$duration,$audio_file,$channels) = extract_mkv($opt_in, $tmp_h264, 0,0);

# modify h264 header to change level_idc to 0x29
tprint("Changing h.264 stream's level_idc header...\n");
change_h264_level($tmp_h264);

tprint("Converting audio to aac...\n");
conv_to_aac($audio_file, $tmp_aac, $channels);

tprint("Creating mp4 file ($opt_out)...\n");
create_mp4($tmp_h264, $tmp_aac, $vid_fps, $tmp_mp4, $opt_out);

# cleanup and finsh processing
tprint("Cleaning up tmp files...\n");
tprint("(files $tmp_ac3,$tmp_h264,$tmp_wav_fifo,$tmp_aac,$tmp_mp4) ... \n");
unlink($tmp_ac3,$tmp_h264,$tmp_wav_fifo,$tmp_aac,$tmp_mp4);
tprint("Done!\n");

##############################################################################
# check the mkv file format
##############################################################################
sub check_resolution {
   my $mkv = shift;

   my $output = `mkvinfo "$mkv" 2>&1`;
   chomp($output);

   my $width = 0;
   if($output =~ /Pixel width:\s+(\d+)/i) {
      $width = $1;
      print "MSG - MkvInfo pixel width - $width \n";
   }
   if($width == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   my $height = 0;
   if($output =~ /Pixel height:\s+(\d+)/i) {
      $height = $1;
      print "MSG - MkvInfo pixel height - $height \n";
   }
   if($height == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   #if($height % 16) {
   #   print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
   #   print "Consider using ffmpeg/mencoder to crop this video first.\n";
   #   exit 1;
   #}
}

##############################################################################
# extract the video and audio raw tracks from the mkv continer
##############################################################################
sub extract_mkv {
   my ($in, $h264, $dont_extract, $channels) = @_;

   my $fps = -1;
   my $duration = -1;
   my $type = undef;
   my $audio_type = undef;
   my $video_type = undef;

   my ($audio_track_num, $h264_track_num) = (-1, -1);
   my ($found_video, $found_audio) = (0,0);

   my $cur_audio = 0;
   my $cur_video = 0;

   # find out which track is which
   my $curr_track_num = -1;

   my @output = `mkvinfo "$in" 2>&1`;
   chomp(@output);
   foreach my $line (@output) {
      if($found_video && $channels && $found_audio && $fps != -1 && defined $audio_type) {
         last;
      }
      if($line =~ /Default duration.*\((\d+\.\d+)\s*fps/i) {
         my $tmp = $1;
         if($type =~ /video/i) {
            $fps = $tmp;
         }
      } elsif($line =~ /^\s*\|\s*\+\s*Duration:\s*(\d+\.\d+)\s*s\s+/i) {
         $duration = $1;
      } elsif($line =~ /Track number:\s+(\d+)/i) {
         $curr_track_num = $1;
         next;
      } elsif($line =~ /Track type:\s+(\S+)/i) {
         if($curr_track_num == -1) {
            # we haven't found the track # yet, but we found the type.
            # this shouldn't happen
            print "Error, mkvinfo failed.\n";
            exit 1;
         }
         $type = $1;
         if($type =~ /audio/i) {
            if(! $found_audio) {
               $audio_track_num = $curr_track_num;
               $found_audio = 1;
               $cur_video = 0;
               $cur_audio = 1;
            }
         } else {
            if(! $found_video) {
               $h264_track_num = $curr_track_num;
               $found_video = 1;
               $cur_video = 1;
               $cur_audio = 0;
            }
         }
      } elsif($found_audio && $cur_audio && $line =~ /Codec ID:\s+(\S+)/i) {
         $audio_type = $1;
         print "MSG - MkvInfo Audio - $audio_type Track: $audio_track_num\n";
      } elsif($found_video && $cur_video && $line =~ /Codec ID:\s+(\S+)/i) {
         $video_type = $1;
         print "MSG - MkvInfo Video - $video_type Track: $h264_track_num\n";
      }

      if ($line =~ /Channels:\s+(\d+)/i) {
         $channels = $1;
         if ($channels == 6) {
            print "MSG - MkvInfo Audio Channels - (Dolby 5.1 / DTS)\n";
         } else {
            print "MSG - MkvInfo Audio Channels - (Stereo 2.1)\n";
         }
      }
   }

   if($fps == -1 || $duration == -1 || $audio_track_num == -1 || $h264_track_num == -1) {
      print "mkvinfo parsing failed. mkvinfo output:\n\n" . join("\n", @output), "\n";
      exit 1;
   }

   my $audio_file;
   if($audio_type eq "A_DTS") {
      $audio_file = $tmp_dts;
   } elsif($audio_type eq "A_AC3") {
      $audio_file = $tmp_ac3;
   } else {
      print "Error: invalid audio type in mkv: $audio_type\n";
      exit 1;
   }

   print "mkvextract tracks \"$in\" $audio_track_num:$audio_file $h264_track_num:$tmp_h264\n";

   my $output = `mkvextract tracks "$in" $audio_track_num:$audio_file $h264_track_num:$tmp_h264 2>&1`;

   if($?) {
      print "Error, mkvextract failed! output:\n\n$output\n";
      exit 1;
   }

   if($fps == -1) {
      print "Error, could not determine input MKV fps\n";
      exit 1;
   }

   return ($fps, $duration, $audio_file, $channels);
}

##############################################################################
# change h264 header level_idc to 0x29
##############################################################################
sub change_h264_level {
   my $file = shift;
   open my $fh, "+< $file" or die "Cannot open temporary h264 file\n";
   sysseek($fh, 7, 0);
   syswrite($fh,"\x29",1);
   close($fh);
}

##############################################################################
# convert audio AC3 -> WAV -> AAC
##############################################################################
sub conv_to_aac {
   my ($in, $aac, $channels) = @_;

   my $fifo = $tmp_wav_fifo;

   if ($channels == 6) {
      print "mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo\n";

      my $output = `mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo 2>&1`;

      if($?) {
         tprint("mplayer/faac conversion to aac failed: $output\n");
         exit 1;
      }
   } else {
      print "mplayer $in -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo\n";

      my $output = `mplayer $in -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo 2>&1`;

      if($?) {
         tprint("mplayer/faac conversion to aac failed: $output\n");
         exit 1;
      }
   }

   my $faac_cmd = "faac -q 100 -o \"$aac\" \"$fifo\"";
   print "$faac_cmd\n";
   system($faac_cmd);
   # clean up the fifo and the ac3/dts file to save on disk space
   unlink($in);
   unlink($fifo);
}

##############################################################################
# remux the video and audio tracks in the mp4 format
##############################################################################
sub create_mp4 {
   my ($h264, $aac, $fps, $tmp_mp4, $outf) = @_;

   # size of h264 + aac
   my $total_size = 0;

   # split the file into 3.5 G chunks to avoid problems with
   # PS3 playback of 4G files, this is the size in KB
   my $split_size = 4000000;

   my $split = 0;

   # find out how big the existing file is. If it's less than
   # our split size, then don't bother splitting it
   my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
      $atime,$mtime,$ctime,$blksize,$blocks) = stat($h264);

   $total_size += $size;

   ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
      $atime,$mtime,$ctime,$blksize,$blocks) = stat($aac);

   $total_size += $size;

   # normalize to KB for comparison
   $total_size /= 1024;
   if($total_size > $split_size) {
      $split = 1;
   }

   my $split_str = "";
   if($split) {
      $split_str = "-splits $split_size";
   } else {
      $split_str = "";
   }

   my $cmd = "MP4Box $split_str -add $h264 -add $aac -fps $fps -par 1=1:1 -lang eng \"$outf\"";
   print "$cmd\n";

   #my $output = `$cmd`;
   my $output = system($cmd);
   if($?) {
      print "MP4Box creation of mp4 failed! output:\n\n$output\n";
      exit 1;
   }
}

##############################################################################
# make sure we have all the tools for the job
##############################################################################
sub check_required_tools {

   my $errors = 0;

   my @required = qw(mkvinfo mkvextract ffmpeg mplayer MP4Box faac);
   foreach my $req_prog (@required) {
      my $found = 0;
      foreach my $path_ent (split(/:/, $ENV{PATH})) {
         if(-r "$path_ent/$req_prog") {
            $found = 1;
            last;
         }
      }
      if(! $found) {
         $errors++;
         print "Error, required program: $req_prog not found. Please install it.\n";
      }
   }

   if($errors > 0) {
      exit 1;
   }
}

##############################################################################
# print status messages during remux process
##############################################################################
sub tprint {
   my $msg = shift;

   print $msg;
}

```

The script had a glitch with tmp files (was naming the tmpfile as the final output hence deleting it...), now should be ok.
I tested a small segment of a 1280x534 mkv ==> mp4 and that works great on the PS3.
My only concern is that I haven't used the script yet to demux->mux a bigger mkv (maybe faac could introduce audio lag? In that case we could be forced to use neroAaacEnc :-( ...) .
Give it a try and let me know. Hope is ok!

Cheers ;-)

---

### Post by encore2097 on 2009-12-16
> **Emanuele_Z said:**
> Hi guys,
The script had a glitch with tmp files (was naming the tmpfile as the final output hence deleting it...), now should be ok.
I tested a small segment of a 1280x534 mkv ==> mp4 and that works great on the PS3.
My only concern is that I haven't used the script yet to demux->mux a bigger mkv (maybe faac could introduce audio lag? In that case we could be forced to use neroAaacEnc :-( ...) .
Give it a try and let me know. Hope is ok!

Cheers ;-)

Gave it a try, output follows:

Checking input file format...
MSG - MkvInfo pixel width - 1280
MSG - MkvInfo pixel height - 720
Extracting mkv file...
MSG - MkvInfo Video - V_MPEG4/ISO/AVC Track: 1
MSG - MkvInfo Audio - A_AAC Track: 2
MSG - MkvInfo Audio Channels - (Stereo 2.1)
Error: invalid audio type in mkv: A_AAC

---

### Post by wheniwork on 2009-12-31
> **Emanuele_Z said:**
> Hi guys,

after some searching around I found out a script in a post of 2008 (now locked).
That script needed some mkv... tools, MP4Box and neroAacEnc (closed source but free). It had a constraint to produce video files whose sizes (x and y) had to be divisible by 16; luckily the newer PS3 OS will support all the sizes.
Then I didn't like to use closed source binary neroAacEnc, so I replaced the command line with the equivalent faac.
Naturally the script won't touch the video stream (no re-encoding): will only convert the audio stream to AAC.

To run the script you'll need the following:
```
sudo apt-get install mkvtoolnix gpac faac ffmpeg
```

Following is the script:
```

#!/usr/bin/perl
#######################################################################
#
#  File:        mkv2mp4.pl
#  Author(s):   Justin Randall (randall311 AT yahoo DOT com)
#               Josh Carroll   (josh.carroll AT gmail DOT com)
#  Version:     0.1
#  Created:     29 April 2008
#  Last Change: Wed May 14 10:00 PM 2008 EDT
#  Description: This script takes an MKV file as input and produces
#               a MP4 (h264/aac) which will play back on the
#               Sony PlayStation 3 (tm)
#  Usage:       mkv2mp4.pl <maktrosa input file>
#  History:     none
#
#  Copyright (c) 2008 by Josh Carroll (josh.carroll AT gmail DOT com)
#  under the name mkv4ps3.  This is a highly modified version used to
#  produce an MP4 (h264/aac) from a mkv file in an automated fashion
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
#  GNU General Public License for more details.
#
#######################################################################
use warnings;
use strict;
use Getopt::Long;
use POSIX qw(floor);
use Cwd qw(realpath);
use File::Basename;

my $prog = $0;
$prog =~ s/.*\///img;

if ($#ARGV != 0) {
   print "Usage: $prog <maktrosa input file>\n";
   exit 0;
}

# set the input based off the command arguments
my $opt_in = $ARGV[0];

my($name, $path, $suffix) = fileparse($opt_in, qr{\..*});

if ($suffix eq '') {
   print "input file did not contain a suffix!\n";
   exit -1;
}

# remove file extension from input file
my $char = 0;
my $basename = $opt_in;
while ($char ne '.') {
   $char = chop $basename;
}

# temoprary files and variables
my $opt_tmp = $basename;
$opt_tmp = "$opt_tmp";
my $opt_out = "$basename.mp4";
my $tmp_ac3 = "$name.ac3";
my $tmp_dts = "$name.dts";
my $tmp_h264 = "$name.h264";
my $tmp_wav_fifo = "$name.wav";
my $tmp_aac = "$name.aac";
my $tmp_mp4 = "t.$name.mp4";

# make sure we have all the tools
check_required_tools();

# make sure the mkv file is correct format
tprint("Checking input file format...\n");
check_resolution($opt_in);

tprint("Extracting mkv file...\n");
# get the fps of the video and the duration (in seconds) of the MKV, and
#	extract the mkv (if only re-muxing to mp4 with aac)
my ($vid_fps,$duration,$audio_file,$channels) = extract_mkv($opt_in, $tmp_h264, 0,0);

# modify h264 header to change level_idc to 0x29
tprint("Changing h.264 stream's level_idc header...\n");
change_h264_level($tmp_h264);

tprint("Converting audio to aac...\n");
conv_to_aac($audio_file, $tmp_aac, $channels);

tprint("Creating mp4 file ($opt_out)...\n");
create_mp4($tmp_h264, $tmp_aac, $vid_fps, $tmp_mp4, $opt_out);

# cleanup and finsh processing
tprint("Cleaning up tmp files...\n");
tprint("(files $tmp_ac3,$tmp_h264,$tmp_wav_fifo,$tmp_aac,$tmp_mp4) ... \n");
unlink($tmp_ac3,$tmp_h264,$tmp_wav_fifo,$tmp_aac,$tmp_mp4);
tprint("Done!\n");

##############################################################################
# check the mkv file format
##############################################################################
sub check_resolution {
   my $mkv = shift;

   my $output = `mkvinfo "$mkv" 2>&1`;
   chomp($output);

   my $width = 0;
   if($output =~ /Pixel width:\s+(\d+)/i) {
      $width = $1;
      print "MSG - MkvInfo pixel width - $width \n";
   }
   if($width == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   my $height = 0;
   if($output =~ /Pixel height:\s+(\d+)/i) {
      $height = $1;
      print "MSG - MkvInfo pixel height - $height \n";
   }
   if($height == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   #if($height % 16) {
   #   print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
   #   print "Consider using ffmpeg/mencoder to crop this video first.\n";
   #   exit 1;
   #}
}

##############################################################################
# extract the video and audio raw tracks from the mkv continer
##############################################################################
sub extract_mkv {
   my ($in, $h264, $dont_extract, $channels) = @_;

   my $fps = -1;
   my $duration = -1;
   my $type = undef;
   my $audio_type = undef;
   my $video_type = undef;

   my ($audio_track_num, $h264_track_num) = (-1, -1);
   my ($found_video, $found_audio) = (0,0);

   my $cur_audio = 0;
   my $cur_video = 0;

   # find out which track is which
   my $curr_track_num = -1;

   my @output = `mkvinfo "$in" 2>&1`;
   chomp(@output);
   foreach my $line (@output) {
      if($found_video && $channels && $found_audio && $fps != -1 && defined $audio_type) {
         last;
      }
      if($line =~ /Default duration.*\((\d+\.\d+)\s*fps/i) {
         my $tmp = $1;
         if($type =~ /video/i) {
            $fps = $tmp;
         }
      } elsif($line =~ /^\s*\|\s*\+\s*Duration:\s*(\d+\.\d+)\s*s\s+/i) {
         $duration = $1;
      } elsif($line =~ /Track number:\s+(\d+)/i) {
         $curr_track_num = $1;
         next;
      } elsif($line =~ /Track type:\s+(\S+)/i) {
         if($curr_track_num == -1) {
            # we haven't found the track # yet, but we found the type.
            # this shouldn't happen
            print "Error, mkvinfo failed.\n";
            exit 1;
         }
         $type = $1;
         if($type =~ /audio/i) {
            if(! $found_audio) {
               $audio_track_num = $curr_track_num;
               $found_audio = 1;
               $cur_video = 0;
               $cur_audio = 1;
            }
         } else {
            if(! $found_video) {
               $h264_track_num = $curr_track_num;
               $found_video = 1;
               $cur_video = 1;
               $cur_audio = 0;
            }
         }
      } elsif($found_audio && $cur_audio && $line =~ /Codec ID:\s+(\S+)/i) {
         $audio_type = $1;
         print "MSG - MkvInfo Audio - $audio_type Track: $audio_track_num\n";
      } elsif($found_video && $cur_video && $line =~ /Codec ID:\s+(\S+)/i) {
         $video_type = $1;
         print "MSG - MkvInfo Video - $video_type Track: $h264_track_num\n";
      }

      if ($line =~ /Channels:\s+(\d+)/i) {
         $channels = $1;
         if ($channels == 6) {
            print "MSG - MkvInfo Audio Channels - (Dolby 5.1 / DTS)\n";
         } else {
            print "MSG - MkvInfo Audio Channels - (Stereo 2.1)\n";
         }
      }
   }

   if($fps == -1 || $duration == -1 || $audio_track_num == -1 || $h264_track_num == -1) {
      print "mkvinfo parsing failed. mkvinfo output:\n\n" . join("\n", @output), "\n";
      exit 1;
   }

   my $audio_file;
   if($audio_type eq "A_DTS") {
      $audio_file = $tmp_dts;
   } elsif($audio_type eq "A_AC3") {
      $audio_file = $tmp_ac3;
   } else {
      print "Error: invalid audio type in mkv: $audio_type\n";
      exit 1;
   }

   print "mkvextract tracks \"$in\" $audio_track_num:$audio_file $h264_track_num:$tmp_h264\n";

   my $output = `mkvextract tracks "$in" $audio_track_num:$audio_file $h264_track_num:$tmp_h264 2>&1`;

   if($?) {
      print "Error, mkvextract failed! output:\n\n$output\n";
      exit 1;
   }

   if($fps == -1) {
      print "Error, could not determine input MKV fps\n";
      exit 1;
   }

   return ($fps, $duration, $audio_file, $channels);
}

##############################################################################
# change h264 header level_idc to 0x29
##############################################################################
sub change_h264_level {
   my $file = shift;
   open my $fh, "+< $file" or die "Cannot open temporary h264 file\n";
   sysseek($fh, 7, 0);
   syswrite($fh,"\x29",1);
   close($fh);
}

##############################################################################
# convert audio AC3 -> WAV -> AAC
##############################################################################
sub conv_to_aac {
   my ($in, $aac, $channels) = @_;

   my $fifo = $tmp_wav_fifo;

   if ($channels == 6) {
      print "mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo\n";

      my $output = `mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo 2>&1`;

      if($?) {
         tprint("mplayer/faac conversion to aac failed: $output\n");
         exit 1;
      }
   } else {
      print "mplayer $in -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo\n";

      my $output = `mplayer $in -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo 2>&1`;

      if($?) {
         tprint("mplayer/faac conversion to aac failed: $output\n");
         exit 1;
      }
   }

   my $faac_cmd = "faac -q 100 -o \"$aac\" \"$fifo\"";
   print "$faac_cmd\n";
   system($faac_cmd);
   # clean up the fifo and the ac3/dts file to save on disk space
   unlink($in);
   unlink($fifo);
}

##############################################################################
# remux the video and audio tracks in the mp4 format
##############################################################################
sub create_mp4 {
   my ($h264, $aac, $fps, $tmp_mp4, $outf) = @_;

   # size of h264 + aac
   my $total_size = 0;

   # split the file into 3.5 G chunks to avoid problems with
   # PS3 playback of 4G files, this is the size in KB
   my $split_size = 4000000;

   my $split = 0;

   # find out how big the existing file is. If it's less than
   # our split size, then don't bother splitting it
   my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
      $atime,$mtime,$ctime,$blksize,$blocks) = stat($h264);

   $total_size += $size;

   ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
      $atime,$mtime,$ctime,$blksize,$blocks) = stat($aac);

   $total_size += $size;

   # normalize to KB for comparison
   $total_size /= 1024;
   if($total_size > $split_size) {
      $split = 1;
   }

   my $split_str = "";
   if($split) {
      $split_str = "-splits $split_size";
   } else {
      $split_str = "";
   }

   my $cmd = "MP4Box $split_str -add $h264 -add $aac -fps $fps -par 1=1:1 -lang eng \"$outf\"";
   print "$cmd\n";

   #my $output = `$cmd`;
   my $output = system($cmd);
   if($?) {
      print "MP4Box creation of mp4 failed! output:\n\n$output\n";
      exit 1;
   }
}

##############################################################################
# make sure we have all the tools for the job
##############################################################################
sub check_required_tools {

   my $errors = 0;

   my @required = qw(mkvinfo mkvextract ffmpeg mplayer MP4Box faac);
   foreach my $req_prog (@required) {
      my $found = 0;
      foreach my $path_ent (split(/:/, $ENV{PATH})) {
         if(-r "$path_ent/$req_prog") {
            $found = 1;
            last;
         }
      }
      if(! $found) {
         $errors++;
         print "Error, required program: $req_prog not found. Please install it.\n";
      }
   }

   if($errors > 0) {
      exit 1;
   }
}

##############################################################################
# print status messages during remux process
##############################################################################
sub tprint {
   my $msg = shift;

   print $msg;
}

```

The script had a glitch with tmp files (was naming the tmpfile as the final output hence deleting it...), now should be ok.
I tested a small segment of a 1280x534 mkv ==> mp4 and that works great on the PS3.
My only concern is that I haven't used the script yet to demux->mux a bigger mkv (maybe faac could introduce audio lag? In that case we could be forced to use neroAaacEnc :-( ...) .
Give it a try and let me know. Hope is ok!

Cheers ;-)

Is this script still valid for mkv to PS3 playback? Anyone tried larger MKV files... is audio OK? Is there an updated version that uses the Nero? 

I like the fact that someone has made a script to do this. Doing it manually is way to tedious.... If anyone knows of a better script to do this via the terminal, let us know... thanks.

---

### Post by wheniwork on 2009-12-31
I'm trying it on a 4G mkv. I get an unstable with the audio.. but it's still encoding... we'll see... May need to use Nero for audio.

```
Checking input file format...
MSG - MkvInfo pixel width - 1920 
MSG - MkvInfo pixel height - 1072 
Extracting mkv file...
MSG - MkvInfo Video - V_MPEG4/ISO/AVC Track: 1
MSG - MkvInfo Audio - A_AC3 Track: 2
MSG - MkvInfo Audio Channels - (Dolby 5.1 / DTS)
mkvextract tracks "/media/Movies/MOVIE.mkv" 2:MOVIE.ac3 1:MOVIE.h264
Changing h.264 stream's level_idc header...
Converting audio to aac...
mplayer MOVIE.ac3 -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=MOVIE.wav -channels 6 -novideo
faac -q 100 -o "MOVIE.aac" "MOVIE.wav"
Freeware Advanced Audio Coder
FAAC 1.26.1 (Aug 16 2008) UNSTABLE

Remapping input channels: Center=3, LFE=4
Quantization quality: 100
Bandwidth: 16000 Hz
Object type: Low Complexity(MPEG-2) + M/S
Container format: Transport Stream (ADTS)
Encoding MOVIE.wav to MOVIE.aac
   frame          | bitrate | elapsed/estim | play/CPU | ETA
15650/57911 ( 27%)|   14.6  |   96.1/355.7  |    3.47x | 259.6 

```

---

### Post by wheniwork on 2009-12-31
LOL... the unstable is referring to the software version... I didn't think it though....

---

### Post by laymon on 2010-01-20
Has anyone tried  Arista Transcoder, in the software repository? I am transcoding a tv episode in 720p to .mp4. I will post to let you know how it turns out.:popcorn:

---

### Post by thebrandon on 2010-02-01
I keep running into this problem :

Checking input file format...
MSG - MkvInfo pixel width - 1280 
MSG - MkvInfo pixel height - 720 
Extracting mkv file...
MSG - MkvInfo Audio - A_AC3 Track: 1
MSG - MkvInfo Audio Channels - (Dolby 5.1 / DTS)
MSG - MkvInfo Video - V_MPEG4/ISO/AVC Track: 2
mkvextract tracks "video.mkv" 1:the.ac3 2:the.h264
Changing h.264 stream's level_idc header...
Converting audio to aac...
mplayer the.ac3 -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=the.wav -channels 6 -novideo
faac -q 100 -o "the.aac" "the.wav"
Freeware Advanced Audio Coder
FAAC 1.26.1 (Aug 16 2008) UNSTABLE

the.wav: No such file or directory
Couldn't open input file the.wav
Creating mp4 file (video.mp4)...
Use of uninitialized value $size in addition (+) at ./mkv2mp4.pl line 320.
MP4Box  -add the.h264 -add the.aac -fps 23.976 -par 1=1:1 -lang eng "video.mp4"
AVC-H264 import - frame size 1280 x 720 at 23.976 FPS
Import results: 31035 samples - Slices: 311 I 11459 P 19265 B - 1 SEI - 305 IDR
	Stream uses B-slice references - max frame delay 2
Opening file the.aac failed
Error importing the.aac: Requested URL is not valid or cannot be found
MP4Box creation of mp4 failed! output:

256

---

### Post by TurboZinc on 2010-02-21
> **thebrandon said:**
> I keep running into this problem :

Checking input file format...
MSG - MkvInfo pixel width - 1280 
MSG - MkvInfo pixel height - 720 
Extracting mkv file...
MSG - MkvInfo Audio - A_AC3 Track: 1
MSG - MkvInfo Audio Channels - (Dolby 5.1 / DTS)
MSG - MkvInfo Video - V_MPEG4/ISO/AVC Track: 2
mkvextract tracks "video.mkv" 1:the.ac3 2:the.h264
Changing h.264 stream's level_idc header...
Converting audio to aac...
mplayer the.ac3 -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=the.wav -channels 6 -novideo
faac -q 100 -o "the.aac" "the.wav"
Freeware Advanced Audio Coder
FAAC 1.26.1 (Aug 16 2008) UNSTABLE

the.wav: No such file or directory
Couldn't open input file the.wav
Creating mp4 file (video.mp4)...
Use of uninitialized value $size in addition (+) at ./mkv2mp4.pl line 320.
MP4Box  -add the.h264 -add the.aac -fps 23.976 -par 1=1:1 -lang eng "video.mp4"
AVC-H264 import - frame size 1280 x 720 at 23.976 FPS
Import results: 31035 samples - Slices: 311 I 11459 P 19265 B - 1 SEI - 305 IDR
    Stream uses B-slice references - max frame delay 2
Opening file the.aac failed
Error importing the.aac: Requested URL is not valid or cannot be found
MP4Box creation of mp4 failed! output:

256
bump

---

### Post by nah40 on 2010-02-21
I think Handbrake will do the job for you.
Google for it.

---

### Post by genfly on 2010-02-25
Hrm i'm getting an error :S
Could anyone please tell me what's going wrong? It would be amazing to get it working!

```
perl mkv2mp4.pl file.mkv
Checking input file format...
MSG - MkvInfo pixel width - 1280 
MSG - MkvInfo pixel height - 720 
Extracting mkv file...
MSG - MkvInfo Video - V_MPEG4/ISO/AVC Track: 1
MSG - MkvInfo Audio - A_AC3 Track: 2
MSG - MkvInfo Audio Channels - (Dolby 5.1 / DTS)
mkvextract tracks "file.mkv" 2:file.ac3 1:file.h264
Changing h.264 stream's level_idc header...
Converting audio to aac...
mplayer file.ac3 -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=file.wav -channels 6 -novideo
faac -q 100 -o "file.aac" "file.wav"
Freeware Advanced Audio Coder
FAAC 1.26.1 (Aug 16 2008) UNSTABLE

file.wav: No such file or directory
Couldn't open input file file.wav
Creating mp4 file (file.mp4)...
Use of uninitialized value $size in addition (+) at mkv2mp4.pl line 320.
MP4Box  -add file.h264 -add file.aac -fps 23.976 -par 1=1:1 -lang eng "file.mp4"
AVC-H264 import - frame size 1280 x 720 at 23.976 FPS
MP4Box: media_tools/av_parsers.c:1902: AVC_ReformatSEI_NALU: Assertion `written<=nal_size' failed.
Aborted
MP4Box creation of mp4 failed! output:

34304

```

Thanks in advance!! :)

---

### Post by nah40 on 2010-02-25
you might try the handbrake forum.
i'm not an expert

---

### Post by genfly on 2010-02-25
ooh ok nice thanks, ill try that now


Edit: Seems to be working. Gonna take a while though to complete :)
Thanks ever so much!!!

---

### Post by afiser on 2011-10-18
> **nah40 said:**
> you might try the handbrake forum.
i'm not an expert

handbrake does not support remuxing (this script does, even though i cannot get it to work) so it's not really a solution.

with handbrake you have to re-encode the entire file for literally no reason, ps3 supports h.264 natively in the mp4 and mt2s containers, all you need to encode usually is the audio if it is not aac already.

---

### Post by oldos2er on 2011-10-18
Closed for necromancy. Please do not bump old threads.

---

