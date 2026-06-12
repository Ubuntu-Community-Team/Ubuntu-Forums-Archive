---
title: "SSH inside CGI"
date: 2011-01-12
forum: General Help
---

### Post by ghostzen on 2011-01-12
Hi all,
so I am building a web page/form using cgi.pm + perl.  I want the internal users to be able to enter in their username and password onto the form in order to log in, which they normally would use a terminal to ssh to it.  How do I get ssh to work in CGI web form?
I have tried Net::SSH::Perl, but I am stuck and needed help.  Please see below(this was the failed test).   

```

#!/usr/bin/perl
use Net::SSH::Perl;

my $host ="rock.abc.xyz" ;
my $user = "test123";
my $pasword = "abc123";

my $ssh = Net::SSH::Perl->new($host);
$ssh->login($user,$password);
my($stdout, $stderr, $exit) = $ssh->cmd($cmd);

```

Ouput:
```

Math::BigInt: couldn't load specified math lib(s), fallback to Math::BigInt::FastCalc at /usr/local/share/perl/5.10.1/Crypt/DH.pm line 6
Permission denied at sshrock.pl line 9


```

Thank you

---

### Post by Michael Vengerovich on 2011-05-11
Was there any solution?
I got the same...

---

