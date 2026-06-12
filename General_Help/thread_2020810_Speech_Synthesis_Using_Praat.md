---
title: "Speech Synthesis Using Praat"
date: 2012-07-08
forum: General Help
---

### Post by dmobley88 on 2012-07-08
I have installed praat, and I understand the tutorial. I also understand that praat is not a TTS program. I do, however, need some help using this software, as it is a bit confusing. I have searched their forums, and there was no solutions found in what I am looking for.

I am wanting to make a high-pitched, natural sounding female voice say, "Hello, how are you?"

Does anyone have any clear, easy to follow (not so confusing) instructions to do this? I would greatly appreciate your help. Thank you for your time and consideration.

---

### Post by frytek on 2012-07-09
> **dmobley88 said:**
> 
I am wanting to make a high-pitched, natural sounding female voice say, "Hello, how are you?"



I don't know much about Praat (yet) but if you just want TTS to get the "Hello...", the easiest way for you to do it is to use espeak + mbrola. 

Gespeaker as a gui could be a good choice. But please notice that you have to set it to use mbrola voice first. There are a few voices for english, some are female.

Gespeaker is the easiest but it has one feature that I consider a bug. There is always a pause between words and there's no way to change its lenght to zero (while you can change speed or pitch). So in my opinion much better results can be achieved with bash scripts "txt to mp3" which use also espeak + mbrola - but everything can be edited. You can find them on the Internet or let me know - I have one somwhere. 


All this, however, is not as good as commercial products. Some of them can be run with wine. 

I also came across a nice script that would send your text, sentence by sentence, to google translate, invoke "listen" on translation page (which uses google TTS, a really good one), record it and connect the sentences in one big mp3 file. But google has made it unusable for long texts, adding captchas on this page. But it should work for your "Hello". 

Here's the script. Save it in a file.pl, make executable and run in a terminal window. 

#!/usr/bin/perl

#--------------------------------------------------
# Usage:
# echo "Hello world" | ./speak.pl en speech.mp3
# cat file.txt       | ./speak.pl en speech.mp3
#
#
# Prerequisites:
# sudo apt-get install libwww-perl sox libsox-fmt-mp3
#
# Compiling sox:
# Older versions of sox package might not have support for mp3 codec,
# so just download sox from [http://sox.sourceforge.net/](http://sox.sourceforge.net/)
# install packages libmp3lame-dev libmad0-dev
# and compile sox
#--------------------------------------------------

use LWP;
use strict;
 
if (scalar(@ARGV) != 2) {
	print STDERR "Usage: $0 LANGUAGE OUT.mp3\n";
	print STDERR "\n";
	print STDERR "Examples: \n";
	print STDERR "    echo \"Hello world\" | ./speak.pl en speech.mp3\n";
	print STDERR "    cat file.txt       | ./speak.pl en speech.mp3\n";
	exit;
}

my $language = $ARGV[0]; #"sk"
my $all_mp3_out = $ARGV[1];
my $TMP_DIR = "$all_mp3_out.tmp";
my $RECAPTCHA_URL = "http://www.google.com/sorry/?continue=http%3A%2F%2Ftranslate.google.com%2Ftranslate_tts%3Ftl=en%26q=Your+identity+was+successfuly+confirmed.";
my $RECAPTCHA_SLEEP_SECONDS = 5;
my $SYSTEM_WEBBROWSER = "firefox";
mkdir $TMP_DIR;

my $silence_duration_paragraphs = 0.8;
my $silence_duration_sentences  = 0.2;
my $silence_duration_comma      = 0.1;
my $silence_duration_brace      = 0.1;
my $silence_duration_semicolon  = 0.2;
my $silence_duration_words      = 0.05;

my @headers = (
'Host' => 'translate.google.com',
'User-Agent' => 'Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.5) Gecko/20091109 Ubuntu/9.10 (karmic) Firefox/3.5.5',
'Accept' => 'text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8',
'Accept-Language' => 'en-us,en;q=0.5',
'Accept-Encoding' => 'gzip,deflate',
'Accept-Charset' => 'ISO-8859-1,utf-8;q=0.7,*;q=0.7',
'Keep-Alive' => '300',
'Connection' => 'keep-alive',
);
 
my $browser = LWP::UserAgent->new;

my @all_mp3s = ();
my $sentence_idx = 0;
# For each input line
while (my $line = <STDIN>)
{
	chomp($line);
	print "line: $line\n";
	# Check for empty lines - paragraphs separator
	if ($line =~ /^\s*$/) {
		push @all_mp3s, SilenceToMp3($sentence_idx++, $silence_duration_paragraphs);
	} else {
		my @words = split(/\s+/, $line);
		my $sentence = "";
		# For each word
		for (my $i=0; $i<scalar(@words); $i++) 
		{
			my $word = $words[$i];
			$sentence .= " $word"; # add another word to the sentence
			my $say = 0;
			my $silence_duration = 0.0;
			if (length($sentence) >= 100) {
				# Remove the last word;
				$sentence = substr($sentence, 0, length($sentence)-length($word)-1); 
				$say = 1;
				$silence_duration = $silence_duration_words;
				$i --; # one word back
			}
			# If a separator was found
			elsif (substr($word, length($word)-1, 1) =~ /[.!?]/ ) {
				$say = 1;
				$silence_duration = $silence_duration_sentences;
			}
			elsif (substr($word, length($word)-1, 1) eq ",") {
				$say = 1;
				$silence_duration = $silence_duration_comma;
			}
			elsif (substr($word, length($word)-1, 1) eq ";") {
				$say = 1;
				$silence_duration = $silence_duration_semicolon;
			}
			elsif (substr($word, length($word)-1, 1) eq ")") {
				$say = 1;
				$silence_duration = $silence_duration_brace;
			}
			# If there are no more words
			elsif ($i == scalar(@words)-1) {
				$say = 1;
				$silence_duration = $silence_duration_words;
			}

			if ($say) {
				push @all_mp3s, TrimSilence( SentenceToMp3($sentence, $sentence_idx++) );
				push @all_mp3s, SilenceToMp3($sentence_idx++, $silence_duration);
				$sentence = ""; # start a new sentence
			}
		}
	}
}

print "Concatenate: @all_mp3s\n";
print "Writing output to $all_mp3_out...";
JoinMp3s(\@all_mp3s, $all_mp3_out);
print "done\n";

sub JoinMp3s() {
	my $mp3s_ref = shift;
	my $mp3_out = shift;

	Exec("sox @{$mp3s_ref} $mp3_out");
}

sub SilenceToMp3() {
	my $idx = shift;
	my $duration = shift;

	my $mp3_out = sprintf("$TMP_DIR/%04d_sil.mp3", $sentence_idx);
	Exec("sox -n -r 22050 $mp3_out trim 0.0 $duration");
	return $mp3_out;
}

sub SentenceToMp3() {
	my $sentence     = shift;
	my $sentence_idx = shift;

	print "sentence: $sentence\n";
	$sentence =~ s/ /+/g;
	if (length($sentence) > 100) {
		die ("ERROR: sentence has more than 100 characters: '$sentence'");
	}
	
	my $mp3_out = sprintf("$TMP_DIR/%04d.mp3", $sentence_idx);
	#print "mp3_out: $mp3_out\n";
	#print "http://translate.google.com/translate_tts?q=$sentence\n";

	my $recaptcha_waiting = 0;
	my $resp;
	while (1) {
		$resp = $browser->get("http://translate.google.com/translate_tts?tl=$language&q=$sentence", @headers);
#		open my $fh, '<', "recaptcha_response.html" or die "error opening file: $!";
#		$resp = do { local $/; <$fh> };
		if ($resp->content =~ "<!DOCTYPE") {
			if (!$recaptcha_waiting) {
				$recaptcha_waiting = 1;
				ReCaptcha();
			}
		} else {
			last;
		}
		sleep($RECAPTCHA_SLEEP_SECONDS);
		PrintWaitingDot();
	}
	if (length($resp->content) == 0) {
		print "EMPTY SENTENCE: '$sentence'\n";
		return "";
	}
	open(FILE,">$mp3_out");
	print FILE $resp->content;
	close(FILE);
	return $mp3_out;
}

sub PrintWaitingDot() {
	select STDOUT;
	print ".";
	$|=1;
}

sub ReCaptcha() {
	print "\n\n--------------------------------------------------\n\n";
	print "  RE-CAPTCHA";
	print "\n\n--------------------------------------------------\n\n";
	print "This URL is going to be opened in your browser:\n";
	print "$RECAPTCHA_URL\n";
	print "\n";
	print "Please, enter the captcha code in your browser's window.\n";
	print "This program will continue automatically then.\n";
	system("$SYSTEM_WEBBROWSER '$RECAPTCHA_URL'");
}

sub TrimSilence() {
	my $mp3 = shift;

	if ($mp3 eq "") {
		return "";
	}

	my $mp3_out = $mp3;
	$mp3_out =~ s/\.mp3$/_trim.mp3/;
	Exec("
	sox $mp3 -p silence 1 0.1 -40d \\
	| sox -p -p reverse \\
	| sox -p -p silence 1 0.1 -40d \\
	| sox -p $mp3_out reverse
	");
	return $mp3_out;
}

sub Exec() {
	my $cmd = shift;
#	print "exec $cmd\n";
	system $cmd;
	return;
}

---

