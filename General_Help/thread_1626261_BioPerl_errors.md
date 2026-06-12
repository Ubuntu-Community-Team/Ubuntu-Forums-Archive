---
title: "BioPerl errors"
date: 2010-11-20
forum: General Help
---

### Post by mindlessbrain on 2010-11-20
I've got Bioperl installed, and I keep on trying to run scripts. Every time I get an error. Most of them look something like this.

If I go into my /user/share/perl/Bio/ directory, I see all the proper files (seqIO, alignIO, so on and so forth), but I'm still getting all these errors.

jill@jill-desktop:~$ perl /home/jill/Desktop/start.pl

------------- EXCEPTION: Bio::Root::Exception -------------
MSG: id does not exist
STACK: Error::throw
STACK: Bio::Root::Root::throw /usr/share/perl5/Bio/Root/Root.pm:368
STACK: Bio::DB::WebDBSeqI::get_Seq_by_id /usr/share/perl5/Bio/DB/WebDBSeqI.pm:168
STACK: Bio::Perl::get_sequence /usr/share/perl5/Bio/Perl.pm:523
STACK: /home/jill/Desktop/start.pl:7

I've downloaded it both from the terminal and from the .deb package. 

Thanks,

mb

---

