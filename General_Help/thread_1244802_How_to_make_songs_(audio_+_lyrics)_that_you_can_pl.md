---
title: "How to make songs (audio + lyrics) that you can play on your TV."
date: 2009-08-19
forum: General Help
---

### Post by nitep on 2009-08-19
How to make worship songs (audio + lyrics) that you can play on your TV. 


This is great for a church home group where you can see the song on your TV and sing along with the music. 

It can also be used through a data projector at church.

I save the VOB files on a data DVD (not video DVD as you can only have 40 songs that way) and play them on my DVD player. I can the select from any of up to 80 or more songs. 

My DVD player has a USB flash connection and on an 8GB flash drive I can put several hundred songs.

I used to use QDVDAuthor but it is very messy and would not work when I upgraded to Ubuntu 9.04 so I decided to write my own program to do it. You only need to install ffmpeg and possibly soxi. The program is in Perl which will be on your system already.

Here is how.

1. Get the songs you want from your CD's. ffmpeg and soxi can handle most audio formats.

2. Get the lyrics from the net or type them up yourself in the form as follows

	(a) for a one screen song

1
Oh, the blood of Jesus! 
Oh, the blood of Jesus! 
Oh, the blood of Jesus! 
It washes white as snow.
end

  
and save it as a simple text file

	(b) for a multi screen song where the lyrics will change on-screen as the song progresses

2
What a friend we have in Jesus, 
all our sins and griefs to bear! 
What a privilege to carry 
everything to God in prayer! 
O what peace we often forfeit,
O what needless pain we bear, 
all because we do not carry 
everything to God in prayer. 
end
51
Have we trials and temptations? 
Is there trouble anywhere? 
We should never be discouraged; 
take it to the Lord in prayer. 
Can we find a friend so faithful 
who will all our sorrows share? 
Jesus knows our every weakness; 
take it to the Lord in prayer. 
end
1:43



   We have number of screens then lyrics and finish time of that screen repeated. You can have many screens. Notice the "end" in both (a) and (b) examples. This must be in lower-case and on a line by itself. The time can be secs or minutes:secs    To get the times just play the audio with totem or whatever. Before that you can use Audacity to change the tempo and or pitch etc of the audio if you wish.



The program is listed below. Save it in a file such as songs.pl  and run it in a terminal with perl songs.pl

At the start of the program listing you will see lines of code to change to suit your computer set-up.

When you run the program it will ask for the song name and show you the lyrics point size and then the lyrics on a background. If the point size is less than 30 then you can split the song into more screens with shorter lines and fewer lines per screen and corrected timings and repeat. The program will show you the lyrics on the background and you can push the right arrow to see all the screens for a multi screen song. You have to close the image viewer before the program will continue. Read through the program listing comments to see where you can make simple changes to suit yourself. Program follows from here. If you select all and paste into an editor the indentation will look better than it does here.

PLEASE NOTE I copied from here and pasted into an editor to check for errors and some random spaces appeared. end_time became end_t ime in 3 places and 1300 became 1 300. I have no idea why but if that happens to you then get the following from my website here :-

[http://universe.witnesstoday.org/Make_DVD.html](http://universe.witnesstoday.org/Make_DVD.html)

I have added some colour to help also.




#################################################################

#!/usr/bin/perl5.10.0

# This program expects to find the folders 

# $temp   $path/songs_audio   $path/songs_video and $path/songs_lyrics

# change the variables $temp and $path to suit yourself

$temp="/home/peter/temp";

$path="/home/peter/church/Home_group";  

#this is the path to the backgrounds, songs_audio folder, songs_lyrics folder and songs_video folder and ogg folder if you are using that

#--------------------------------------------------------------------

# This program expects to find the files  $path/songs_audio/song.mp3 and $path/songs_lyrics/song.txt

# It will produce $path/songs_video/song.VOB   as described 6 lines down you can use other formats than mp3

# Instead of song.txt you will have a name such as because_he_lives.txt and because_he_lives.mp3

#--------------------------------------------------------------------

# The lyrics file structure must be as follows in a simple text file. I use gedit.

# number verses, {verse lines, end, finish time of verse} repeated  (for multi verse song}

# 1, {verse lines, end}  (for 1 verse song)

#--------------------------------------------------------------------

$audio_type="mp3";  
# you can change this to wav or whatever

#--------------------------------------------------------------------

$font="/usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf";  
#    best font, check you have it or change it

#--------------------------------------------------------------------

# This program expects to find $path/background01.jpg  $path/background02.jpg  $path/background03.jpg  etc

$number_backgrounds=25; 

# change this to the maximum number of backgrounds you have available. They are chosen at random.

#################################################################################################

&mydo("rm $temp/temp*");

$tempvobs="";

print "Please give song txt filename ";

chomp ($my_file=<STDIN>);

$stuff="$path/songs_audio/$my_file.$audio_type";

open STUFF, $stuff or die "Cannot open $stuff for read :$!";

close(STUFF);

$go="ssdfs";

while (length($go)>0 ) 	{ &prepare_lyrics_on_background; } 

for $i (1..$number_verses) {$tempvobs="$tempvobs $temp/temp$i.VOB";
     		    &mydo($do_it[$i]);} # produce the video files

if ($number_verses==1){

#	&mydo("ffmpeg2theora -o  $q$path/ogg/$my_file.ogv$q  $vob");  #Note uncomment this line to produce ogg video files which are excellent if you have the codec

	exit;}

&mydo("rm  $temp/temp?.jpg");

&mydo("cat $tempvobs  > $temp/temp.VOB");

#&mydo("ffmpeg -i $temp/temp.VOB -sameq -y -f vob -r 25 -target pal-svcd -acodec copy -vcodec copy $q$path/songs_video/$my_file.VOB$q");    #Use either this line or the 2 following lines also you can change to -target pal-dvd -sameq -aspect 4:3 -acodec ac3  as shown several lines further on for higher quality

&mydo("ffmpeg -i $temp/temp.VOB -pass 1 -an -f rawvideo -y /dev/null");

&mydo("ffmpeg -i $temp/temp.VOB -pass 2 -sameq -y -f vob -r 25 -target pal-svcd -acodec copy -vcodec copy $q$path/songs_video/$my_file.VOB$q");

# &mydo("ffmpeg2theora -o  $q$path/ogg/$my_file.ogv$q $q$temp/temp.VOB$q"); #Note uncomment this line to produce ogg video files which are excellent if you have the codec

#########################################  end of program  ###########


sub prepare_lyrics_on_background
{

$stuff="$path/songs_lyrics/$my_file.txt";

print "$stuff\n";

open STUFF, $stuff or  die "Cannot open $stuff for read :$!";

&get_back_ground;

$back="$path/$background";

print "background = $back\n\n";

$q='"';

$start_time=0;

chomp($number_verses = <STUFF>); 

print "Number verses = $number_verses  \n";

for $i (1..$number_verses) 

	{

	$lyrics="";

	$longest_line=0;

	$number_lines=0; 

	chomp($line = <STUFF>);

	while ($line ne "end")

		{

		if (eof(STUFF)) {print "Error incorrect $q$my_file.txt$q  file structure. Could not find 'end' where expected\n\n";exit;}

		$lyrics=$lyrics."$line\n";

		if (length($line)>$longest_line){$longest_line=length($line);}

		chomp($line = <STUFF>);

		$number_lines++;

		}

	$point_size=100;

	if ($number_lines*$point_size>340)   {$point_size=int(340/$number_lines);}  # height

	if ($longest_line*$point_size>1300){$point_size=int(1300/$longest_line);}  #width

	$strokewidth=int($point_size/5);     # to get a thicker black outline to the characters change the 5 to 4

	if ($point_size>40){$point_size=40;}

	&get_verse_finish_time;

	$run_time=$end_time - $start_time;

	print "start_time=$start_time end_time=$end_time run_time=$run_time Pointsize = $point_size\n\n";

system("convert $back -gravity center -font '$font' -stroke black -strokewidth $strokewidth  -pointsize $point_size -annotate 0 $q$lyrics$q  -font '$font' -stroke  none   -fill white   -pointsize $point_size -annotate 0 $q$lyrics$q $temp/temp$i.jpg");

# uncomment the following line to get the largest but best quality video. You will then need to comment out the alternative line following it. Also change pal- to ntsc- if needed.

#	$do_it[$i] = "ffmpeg -loop_input -i $q$temp/temp$i.jpg$q -t $run_time -ss $start_time  -i $q$path/songs_audio/$my_file.$audio_type$q -y -f vob -r 25 -target pal-dvd -sameq -aspect 4:3 -acodec ac3 $vob";

	$do_it[$i] = "ffmpeg -loop_input -i $q$temp/temp$i.jpg$q -t $run_time -ss $start_time  -i $q$path/songs_audio/$my_file.$audio_type$q -y -f vob -r 25 -target pal-svcd -sameq -aspect 4:3 -acodec mp2 $vob";

#	$do_it2[$i] = "ffmpeg2theora $vob"; #uncomment this line to produce ogg videos

	print "$do_it[$i]\n\n";

	$start_time = $end_time;

	}

&mydo("eog $temp/temp1.jpg");  # This will display the lyrics so you can change them before the coding of the video

print "\n\nPush ENTER to produce the vob files.  or any key and ENTER to repeat  ";

chomp($go =<STDIN>);

}

###################################################################

sub get_verse_finish_time
{if ($number_verses==1)
    {$end_time =`soxi -d "$path/songs_audio/$my_file.$audio_type"`;

     $k=index($end_time,":",3);

     if ($k>0) 
           {$end_time=substr($end_time,3,2)*60+substr($end_time,6);}

     $vob="$q$path/songs_video/$my_file.VOB$q";

     return;
     }

$vob="$q$temp/temp$i.VOB$q";

chomp($end_time = <STUFF>);

if ($number_verses==$i)
    {$end_time =`soxi -d "$path/songs_audio/$my_file.$audio_type"`;

    $k=index($end_time,":",3);

    if ($k>0)
        {$end_time=substr($end_time,3,2)*60+substr($end_time,6);}

    return;
    }

$k=index($end_time,":",0);

if ($k>0) {$end_time=substr($end_time,0,$k)*60+substr($end_time,$k+1,length($end_time));}

}#######################################################################

sub get_back_ground
{

$j=int(rand($number_backgrounds-1))+1;  # Note this is for background files numbered 1 to $number_backgrounds

if ($j<10){$n="0".$j;} else {$n=$j;}

$background="background".$n.".jpg";

}##########################################################################


sub mydo # show and do system call
{

my ($doit)=@_;
print "********************************************\n$doit\n\n";
print "********************************************\n\n";
system($doit);
print"\n*******************************************\n";

}##########################################################################

---

