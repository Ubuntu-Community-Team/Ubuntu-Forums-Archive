---
title: "using WWW::Nike::NikePlus"
date: 2010-04-29
forum: General Help
---

### Post by thebrandon on 2010-04-29
I am trying to make use of the perl module WWW::Nike::NikePlus to retrive the data from my ipod but apparently I have no idea what I am doing.  I installed the package just as the readme said including all the dependencies.  I cant really figure out how to run it, i searched for how to use it and found this :
Example use that retrieves and prints your last run information

  use WWW::Nike::NikePlus;
  my $username = 'my@email.address';
  my $password = 'MySecretPassword';
  my $locale = "en_us";
  
  my $pin = nike_authenticate( $username, $password, $locale );
  unless( $pin ) { print "Authentication failed\n"; }
  
  #Details of the last run
  my ( $unit, $last_run_dist, $last_run_duration_millisecs, 
        $last_run_duration_friendly, $last_run_pace_friendly ) = nike_last_run();
  
  print "Last run: $last_run_dist$unit in $last_run_duration_friendly\n";
  print "Last run pace: $last_run_pace_friendly per $unit\n";

so I put it in a txt file and saved it with the extension .pl and of course I put in all my info in the username password fields then made it executable with the command sudo chmod +x nikeplus.pl and when I try to run it with either ./ or perl I get this output :

brandon@desktop:~/Apps/nikeplus$ ./nikeplus.pl
./nikeplus.pl: line 1: use: command not found
./nikeplus.pl: line 2: my: command not found
./nikeplus.pl: line 3: my: command not found
./nikeplus.pl: line 4: my: command not found
./nikeplus.pl: line 6: syntax error near unexpected token `('
./nikeplus.pl: line 6: `  my $pin = nike_authenticate( $username, $password, $locale );'
brandon@desktop:~/Apps/nikeplus$ perl nikeplus.pl
Use of uninitialized value $ENV{"TEMP"} in concatenation (.) or string at /usr/local/share/perl/5.10.0/WWW/Nike/NikePlus.pm line 10.
Use of uninitialized value $last_run_duration_millisecs in division (/) at /usr/local/share/perl/5.10.0/WWW/Nike/NikePlus.pm line 106.
Use of uninitialized value $last_run_dist in division (/) at /usr/local/share/perl/5.10.0/WWW/Nike/NikePlus.pm line 107.
Use of uninitialized value $last_run_duration_millisecs in division (/) at /usr/local/share/perl/5.10.0/WWW/Nike/NikePlus.pm line 107.
Illegal division by zero at /usr/local/share/perl/5.10.0/WWW/Nike/NikePlus.pm line 107.
brandon@desktop:~/Apps/nikeplus$ 

I dont know what Im doing wrong and well frankly I dont really know what I am doing to start with!  Any help is greatly appreciated!

---

### Post by Portmanteaufu on 2010-04-29
It looks as though you're missing the easily-forgotton "shebang" line (so-called because it starts with "#!"). The first line in your script needs to be:

```

#!/usr/bin/perl

```

That line tells the interpreter what program should be used to read and execute the rest of the file. In this case, we want Perl. Having this allows you to run your program as:

```
./nikeplus.pl
```
instead of
```
perl nikeplus.pl
```

In your case, because you omitted the line, the shell (Bash) tried to read the entire file as though it was written in Bash. If you'd like, you can keep your code the way it is and just run it as 'perl nikeplus.pl' instead.

Make sense?

---

### Post by Portmanteaufu on 2010-04-29
Oops -- I missed that you posted the output of "perl nikeplus.pl". That's what I get for half-reading the original post.

My previous post explains why you can't run it as './nikeplus.pl', but now we can look into why the valid run seems to fail. I'm not familiar with that particular Perl module, but let's see if I can fake it.

It looks like all of the errors being generated are from within the Perl module. That suggests one of two things:

1.) The module itself is buggy
or
2.) You have passed values into the module functions that cause it to crash and burn. Did you copy-paste the example code, or type it in? Is it possible we're missing some values?

<Also, as a further aside: In Linux, file extensions don't really matter. They're there to help you, the human, remember what a file is for, but strictly speaking the system doesn't use them to determine what to do with a file. Gnome, the graphical user interface, will use them to determine what icon to display and check whether it's a common media format like an mp3, but you can name your programs whatever you'd like.>

---

