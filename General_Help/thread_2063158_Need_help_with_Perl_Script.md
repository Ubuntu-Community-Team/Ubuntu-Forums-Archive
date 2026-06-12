---
title: "Need help with Perl Script"
date: 2012-09-26
forum: General Help
---

### Post by CCgirl6690 on 2012-09-26
Hello everyone 
not sure if its the right forum for this but since people here are friendly and helpful so i decided id give it a try ..
so theres a script i want to use it but i dunno how to save it or how to run it on my computer , here is the code 

> #!/usr/bin/perl  use strict; use warnings;  my %permution = (     "a"  => [ "a", "4", "@", "&", "A" ],     "b" => "bB",     "c" =>  "cC",     "d" => "dD",     "e" => "3Ee",     "f" => "fF",      "g" => "gG9",     "h" => "hH",     "i" => "iI!|1",     "j"  => "jJ",     "k" => "kK",     "l" => "lL!71|",     "m" =>  "mM",     "n" => "nN",     "o" => "oO0",     "p" => "pP",      "q" => "qQ",     "r" => "rR",     "s" => "sS5\$",     "t" =>  "tT71+",     "u" => "uU",     "v" => "vV",     "w" => ["w",  "W", "\\/\\/"],     "x" => "xX",     "y" => "yY",     "z" =>  "zZ2", );  # End config  while(my $word = <>) {     chomp $word;      my @string = split //, lc($word);     &permute(0, @string); }   sub permute {     my $num = shift;     my @str = @_;     my $len = @str;       if($num >= $len) {         foreach my $char (@str) {              print $char;         }         print "\n";         return;     }       my $per = $permution{$str[$num]};      if($per) {         my @letters =  ();         if(ref($per) eq 'ARRAY') {             @letters = @$per;          } else {             @letters = split //, $per;         }          $per = "";          foreach $per (@letters) {             my $s = "";              for(my $i = 0; $i < $len; $i++) {                 if($i eq  0) {                     if($i eq $num) {                         $s =  $per;                     } else {                         $s = $str[0];                      }                 } else {                      if($i eq $num) {                         $s .= $per;                      } else {                         $s .= $str[$i];                     }                  }             }             my @st = split //, $s;              &permute(($num + 1), @st);         }     } else {          &permute(($num + 1), @str);     } }

   thanks for the help

---

### Post by drmrgd on 2012-09-26
Would you mind reposting that,but with CODE tags instead of the QUOTE tags?  Without line breaks and indentation, it's almost impossible to read

Edit:  I just re-read what you posted, and I think I better understand what you're after.  Assuming that the poorly formatted script is a result of bad copy and pasting into the forum and / or the formatting is not going to matter to the script, running it is fairly simple.  Change the permissions on the file to make it executable either in the terminal:

```
chmod +x <yourscript.pl>
```

Or you can use Nautilus by right clicking on the file, going to the properties, and under permissions clicking the box to make it executable.  Then you can simply run it from the terminal by navigating to the file and running:

```
./yourscript.pl
```

or 

```
perl yourscript.pl
```

Hope that helps!

---

### Post by CCgirl6690 on 2012-09-26
here sry 

[HTML] #!/usr/bin/perl  use strict; use warnings;  my %permution = ( 	"a" => [ "a", "4", "@", "&", "A" ], 	"b" => "bB", 	"c" => "cC", 	"d" => "dD", 	"e" => "3Ee", 	"f" => "fF", 	"g" => "gG9", 	"h" => "hH", 	"i" => "iI!|1", 	"j" => "jJ", 	"k" => "kK", 	"l" => "lL!71|", 	"m" => "mM", 	"n" => "nN", 	"o" => "oO0", 	"p" => "pP", 	"q" => "qQ", 	"r" => "rR", 	"s" => "sS5\$", 	"t" => "tT71+", 	"u" => "uU", 	"v" => "vV", 	"w" => ["w", "W", "\\/\\/"], 	"x" => "xX", 	"y" => "yY", 	"z" => "zZ2", );  # End config  while(my $word = <>) { 	chomp $word; 	my @string = split //, lc($word); 	&permute(0, @string); }  sub permute { 	my $num = shift; 	my @str = @_; 	my $len = @str;  	if($num >= $len) { 		foreach my $char (@str) { 			print $char; 		} 		print "\n"; 		return; 	}  	my $per = $permution{$str[$num]};  	if($per) { 		my @letters = (); 		if(ref($per) eq 'ARRAY') { 			@letters = @$per; 		} else { 			@letters = split //, $per; 		} 		$per = "";  		foreach $per (@letters) { 			my $s = ""; 			for(my $i = 0; $i < $len; $i++) { 				if($i eq 0) { 					if($i eq $num) { 						$s = $per; 					} else { 						$s = $str[0]; 					} 				} else { 					if($i eq $num) { 						$s .= $per; 					} else { 						$s .= $str[$i]; 					} 				} 			} 			my @st = split //, $s; 			&permute(($num + 1), @st); 		} 	} else { 		&permute(($num + 1), @str); 	} }[/HTML]

---

### Post by CCgirl6690 on 2012-09-26
or here is a link to the scropt if im allowed to
[http://www.backtrack-linux.org/forums/showthread.php?t=19933](http://www.backtrack-linux.org/forums/showthread.php?t=19933)
question is how do i save it ? 

thank you drmgd

---

### Post by drmrgd on 2012-09-26
> **CCgirl6690 said:**
> or here is a link to the scropt if im allowed to
[http://www.backtrack-linux.org/forums/showthread.php?t=19933](http://www.backtrack-linux.org/forums/showthread.php?t=19933)
question is how do i save it ? 

thank you drmgd

Thanks for the link, that was very helpful!  Here's a copy of the Perl script without the improper line breaks (or lack there of!).  I put a .txt extension on it so that I could upload it to the forum as an attachment.  You might choose to change the extension to '.pl', although Linux doesn't really need the extensions to know what to do with a file.  

You just need to put it in a place where you want to use it, change the permissions as I described above, and then run it as described in the post:

```
perl permute.pl < dictionary.txt
```

Where dictionary.txt is a list of words that you want to stream into the script.  As this thing seems to generate quite a list, you might also consider streaming the output to a new file:

```
perl permute.pl < dictionary.txt > output.txt
```

Hope that helps!

---

### Post by CCgirl6690 on 2012-09-26
Thank you so much , it worked 
................................................................................................................

---

### Post by CCgirl6690 on 2012-09-26
sry again , i tried perl permute.pl wordlist.txt new.txt 
but where does it save teh new created wordlist? i couldnt find it 
can you please test it for yourself and tell me how to ,
thanks again................

---

### Post by drmrgd on 2012-09-26
If you run it as I have it above, then it should save the output file in the same location.  That worked for me at least, although my query may have been different.  I think I just used a single word in my "dictionary" like "something".

---

### Post by Lars Noodén on 2012-09-26
Remember the redirects that drmrgd showed.  You have read < and overwrite >

```

./permute.pl < wordlist.txt > new.txt 

```

There is also append >> but that is not used in this case.

---

### Post by CCgirl6690 on 2012-09-26
ok thanks . i thought  i had to remove these " < >" now it worked with them
thank again you 2
:)))

---

### Post by drmrgd on 2012-09-26
OH!  I apologize!  Sorry I wasn't clear about the need for those redirects.  Glad you got it working (thanks Lars for the help!).

Have fun!

---

