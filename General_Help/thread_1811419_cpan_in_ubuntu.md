---
title: "cpan in ubuntu"
date: 2011-07-24
forum: General Help
---

### Post by itba on 2011-07-24
hi,
can I get help with CPAN's Finance::QuoteHist module on this forum....

---

### Post by blueridgedog on 2011-07-24
You may want to write the author and ask if there is a mailing list relative to the module.

[http://search.cpan.org/dist/Finance-QuoteHist/lib/Finance/QuoteHist.pm](http://search.cpan.org/dist/Finance-QuoteHist/lib/Finance/QuoteHist.pm)

---

### Post by itba on 2011-07-25
I did...no response from them....funny why they complain that Perl is not popular.....

anyways, here is the error message in case anyone can help me out
when I run install Finance::QuoteHist on the cpan prompt, this is what I get:


```

                                 CPAN: Storable loaded ok (v2.20) 
 Going to read '/home/ar/.cpan/Metadata' 
   Database was generated on Sun, 24 Jul 2011 11:27:10 GMT 
 Running install for module 'Finance::QuoteHist' 
 CPAN: Data::Dumper loaded ok (v2.124) 
 'YAML' not installed, falling back to Data::Dumper and Storable to read prefs '/home/ar/.cpan/prefs' 
 Running make for M/MS/MSISK/Finance-QuoteHist-1.16.tar.gz 
 CPAN: Digest::SHA loaded ok (v5.47) 
 CPAN: Compress::Zlib loaded ok (v2.02) 
 Checksum for /home/ar/.cpan/sources/authors/id/M/MS/MSISK/Finance-QuoteHist-1.16.tar.gz ok 
 Scanning cache /home/ar/.cpan/build for sizes 
 ............................................................................DONE 
 CPAN: Archive::Tar loaded ok (v1.52) 
 Finance-QuoteHist-1.16/ 
 Finance-QuoteHist-1.16/t/ 
 Finance-QuoteHist-1.16/t/dat/ 
 Finance-QuoteHist-1.16/t/dat/quote_daily_businessweek.dat 
 Finance-QuoteHist-1.16/t/dat/split_investopedia.dat 
 Finance-QuoteHist-1.16/t/dat/csv.dat 
 Finance-QuoteHist-1.16/t/dat/quote_monthly_yahoo.dat 
 Finance-QuoteHist-1.16/t/dat/quote_daily_google.dat 
 Finance-QuoteHist-1.16/t/dat/quote_weekly_google.dat 
 Finance-QuoteHist-1.16/t/dat/dividend_yahoo.dat 
 Finance-QuoteHist-1.16/t/dat/quote_monthly_msn.dat 
 Finance-QuoteHist-1.16/t/dat/dividend_investopedia.dat 
 Finance-QuoteHist-1.16/t/dat/split_yahoo.dat 
 Finance-QuoteHist-1.16/t/dat/quote_daily_yahoo.dat 
 Finance-QuoteHist-1.16/t/dat/dividend_plain.dat 
 Finance-QuoteHist-1.16/t/dat/quote_weekly_msn.dat 
 Finance-QuoteHist-1.16/t/dat/quote_daily_stocknod.dat 
 Finance-QuoteHist-1.16/t/dat/quote_weekly_yahoo.dat 
 Finance-QuoteHist-1.16/t/dat/split_plain.dat 
 Finance-QuoteHist-1.16/t/dat/quote_daily_investopedia.dat 
 Finance-QuoteHist-1.16/t/dat/quote_daily_msn.dat 
 Finance-QuoteHist-1.16/t/dat/quote_daily_plain.dat 
 Finance-QuoteHist-1.16/t/dat/quote_monthly_businessweek.dat 
 Finance-QuoteHist-1.16/t/dat/quote_weekly_businessweek.dat 
 Finance-QuoteHist-1.16/t/05_csv.t 
 Finance-QuoteHist-1.16/t/30_splits.t 
 Finance-QuoteHist-1.16/t/10_quotes.t 
 Finance-QuoteHist-1.16/t/testload.pm 
 Finance-QuoteHist-1.16/t/00_basic.t 
 Finance-QuoteHist-1.16/t/20_dividends.t 
 Finance-QuoteHist-1.16/lib/ 
 Finance-QuoteHist-1.16/lib/Finance/ 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist.pm 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/ 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/QuoteMedia.pm 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/StockNod.pm 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/Yahoo/ 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/Yahoo/Australia.pm 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/MSN.pm 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/Google.pm 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/Yahoo.pm 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/Investopedia.pm 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/Generic.pm 
 Finance-QuoteHist-1.16/lib/Finance/QuoteHist/BusinessWeek.pm 
 Finance-QuoteHist-1.16/README 
 Finance-QuoteHist-1.16/Changes 
 Finance-QuoteHist-1.16/Makefile.PL 
 Finance-QuoteHist-1.16/META.yml 
 Finance-QuoteHist-1.16/MANIFEST 
 CPAN: File::Temp loaded ok (v0.22) 
  
   CPAN.pm: Going to build M/MS/MSISK/Finance-QuoteHist-1.16.tar.gz 
  
 Note: This is not required, but installing Text::CSV_XS on your system 
       will speed up the parsing of quote data in CSV format. A C 
       compiler is necessary, however. In the meantime we will use 
       Text::CSV_PP. 
 Checking if your kit is complete... 
 Looks good 
 Warning: prerequisite Regexp::Common 0 not found. 
 Warning: prerequisite Text::CSV 0 not found. 
 Writing Makefile for Finance-QuoteHist 
 Could not read '/home/ar/.cpan/build/Finance-QuoteHist-1.16-CDmEVD/META.yml'. Falling back to other methods to determine prerequisites 
 ---- Unsatisfied dependencies detected during ---- 
 ----    MSISK/Finance-QuoteHist-1.16.tar.gz   ---- 
     Regexp::Common [requires] 
     Text::CSV [requires] 
 Shall I follow them and prepend them to the queue 
 of modules we are processing right now? [yes]  y
 Running make test 
   Delayed until after prerequisites 
 Running make install 
   Delayed until after prerequisites 
 Running install for module 'Regexp::Common' 
 'YAML' not installed, falling back to Data::Dumper and Storable to read prefs '/home/ar/.cpan/prefs' 
 Running make for A/AB/ABIGAIL/Regexp-Common-2011041701.tar.gz 
 Checksum for /home/ar/.cpan/sources/authors/id/A/AB/ABIGAIL/Regexp-Common-2011041701.tar.gz ok 
 Regexp-Common-2011041701/ 
 Regexp-Common-2011041701/COPYRIGHT.AL 
 Regexp-Common-2011041701/Makefile.PL 
 Regexp-Common-2011041701/COPYRIGHT.MIT 
 Regexp-Common-2011041701/TODO 
 Regexp-Common-2011041701/MANIFEST 
 Regexp-Common-2011041701/Changes 
 Regexp-Common-2011041701/COPYRIGHT.AL2 
 Regexp-Common-2011041701/t/ 
 Regexp-Common-2011041701/t/URI/ 
 Regexp-Common-2011041701/t/URI/wais.t 
 Regexp-Common-2011041701/t/URI/telnet.t 
 Regexp-Common-2011041701/t/URI/file.t 
 Regexp-Common-2011041701/t/URI/news.t 
 Regexp-Common-2011041701/t/URI/http.t 
 Regexp-Common-2011041701/t/URI/prospero.t 
 Regexp-Common-2011041701/t/URI/gopher.t 
 Regexp-Common-2011041701/t/URI/tv.t 
 Regexp-Common-2011041701/t/URI/any.t 
 Regexp-Common-2011041701/t/URI/nntp.t 
 Regexp-Common-2011041701/t/URI/fax.t 
 Regexp-Common-2011041701/t/URI/pop.t 
 Regexp-Common-2011041701/t/URI/tel.t 
 Regexp-Common-2011041701/t/URI/ftp.t 
 Regexp-Common-2011041701/t/test_list.t 
 Regexp-Common-2011041701/t/Common.pm 
 Regexp-Common-2011041701/t/test_sub_named.t 
 Regexp-Common-2011041701/t/test_bases_sep.t 
 Regexp-Common-2011041701/t/test___luhn.t 
 Regexp-Common-2011041701/t/number/ 
 Regexp-Common-2011041701/t/number/decimal.t 
 Regexp-Common-2011041701/t/number/number.t 
 Regexp-Common-2011041701/t/number/integer.t 
 Regexp-Common-2011041701/t/test_profanity.t 
 Regexp-Common-2011041701/t/test_i.t 
 Regexp-Common-2011041701/t/comment/ 
 Regexp-Common-2011041701/t/comment/single_or_multiline.t 
 Regexp-Common-2011041701/t/comment/html.t 
 Regexp-Common-2011041701/t/comment/single_line.t 
 Regexp-Common-2011041701/t/comment/nested.t 
 Regexp-Common-2011041701/t/comment/delimited.t 
 Regexp-Common-2011041701/t/test_delimited.t 
 Regexp-Common-2011041701/t/test_mac.t 
 Regexp-Common-2011041701/t/test_lingua_palindrome.t 
 Regexp-Common-2011041701/t/test_comments.t 
 Regexp-Common-2011041701/t/test_bases.t 
 Regexp-Common-2011041701/t/test_ws.t 
 Regexp-Common-2011041701/t/test_no_import.t 
 Regexp-Common-2011041701/t/zip/ 
 Regexp-Common-2011041701/t/zip/germany.t 
 Regexp-Common-2011041701/t/zip/belgium.t 
 Regexp-Common-2011041701/t/zip/zip.t 
 Regexp-Common-2011041701/t/zip/spain.t 
 Regexp-Common-2011041701/t/zip/greenland.t 
 Regexp-Common-2011041701/t/zip/norway.t 
 Regexp-Common-2011041701/t/zip/italy.t 
 Regexp-Common-2011041701/t/zip/france.t 
 Regexp-Common-2011041701/t/zip/australia.t 
 Regexp-Common-2011041701/t/zip/us.t 
 Regexp-Common-2011041701/t/zip/netherlands.t 
 Regexp-Common-2011041701/t/zip/denmark.t 
 Regexp-Common-2011041701/t/test_keep.t 
 Regexp-Common-2011041701/t/test_balanced.t 
 Regexp-Common-2011041701/t/zzz_60_pod_coverage.t 
 Regexp-Common-2011041701/t/test_domain.t 
 Regexp-Common-2011041701/t/test_roman.t 
 Regexp-Common-2011041701/t/test_sub.t 
 Regexp-Common-2011041701/t/zzz_50_pod.t 
 Regexp-Common-2011041701/t/test_curry.t 
 Regexp-Common-2011041701/t/test_ip.t 
 Regexp-Common-2011041701/t/SEN/ 
 Regexp-Common-2011041701/t/SEN/usa_ssn.t 
 Regexp-Common-2011041701/t/test_squares.t 
 Regexp-Common-2011041701/COPYRIGHT 
 Regexp-Common-2011041701/META.yml 
 Regexp-Common-2011041701/COPYRIGHT.BSD 
 Regexp-Common-2011041701/lib/ 
 Regexp-Common-2011041701/lib/Regexp/ 
 Regexp-Common-2011041701/lib/Regexp/Common.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/ 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/ 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/RFC1808.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/http.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/RFC2396.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/telnet.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/RFC1035.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/RFC2384.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/ftp.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/fax.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/prospero.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/news.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/pop.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/RFC2806.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/file.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/RFC1738.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/tel.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/gopher.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/wais.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI/tv.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/profanity.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/delimited.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/whitespace.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/lingua.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/balanced.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/SEN.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/comment.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/CC.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/net.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/list.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/number.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/URI.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/_support.pm 
 Regexp-Common-2011041701/lib/Regexp/Common/zip.pm 
 Regexp-Common-2011041701/README 
  
   CPAN.pm: Going to build A/AB/ABIGAIL/Regexp-Common-2011041701.tar.gz 
  
 Checking if your kit is complete... 
 Looks good 
 Writing Makefile for Regexp::Common 
 Could not read '/home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/META.yml'. Falling back to other methods to determine prerequisites 
 cp lib/Regexp/Common/URI/news.pm blib/lib/Regexp/Common/URI/news.pm 
 cp lib/Regexp/Common/_support.pm blib/lib/Regexp/Common/_support.pm 
 cp lib/Regexp/Common/balanced.pm blib/lib/Regexp/Common/balanced.pm 
 cp lib/Regexp/Common/URI/ftp.pm blib/lib/Regexp/Common/URI/ftp.pm 
 cp lib/Regexp/Common/comment.pm blib/lib/Regexp/Common/comment.pm 
 cp lib/Regexp/Common/URI/telnet.pm blib/lib/Regexp/Common/URI/telnet.pm 
 cp lib/Regexp/Common/URI/RFC2396.pm blib/lib/Regexp/Common/URI/RFC2396.pm 
 cp lib/Regexp/Common/whitespace.pm blib/lib/Regexp/Common/whitespace.pm 
 cp lib/Regexp/Common/URI/tel.pm blib/lib/Regexp/Common/URI/tel.pm 
 cp lib/Regexp/Common/URI/RFC1035.pm blib/lib/Regexp/Common/URI/RFC1035.pm 
 cp lib/Regexp/Common/profanity.pm blib/lib/Regexp/Common/profanity.pm 
 cp lib/Regexp/Common/URI.pm blib/lib/Regexp/Common/URI.pm 
 cp lib/Regexp/Common/URI/RFC1738.pm blib/lib/Regexp/Common/URI/RFC1738.pm 
 cp lib/Regexp/Common/CC.pm blib/lib/Regexp/Common/CC.pm 
 cp lib/Regexp/Common/URI/RFC2806.pm blib/lib/Regexp/Common/URI/RFC2806.pm 
 cp lib/Regexp/Common.pm blib/lib/Regexp/Common.pm 
 cp lib/Regexp/Common/URI/prospero.pm blib/lib/Regexp/Common/URI/prospero.pm 
 cp lib/Regexp/Common/URI/RFC2384.pm blib/lib/Regexp/Common/URI/RFC2384.pm 
 cp lib/Regexp/Common/list.pm blib/lib/Regexp/Common/list.pm 
 cp lib/Regexp/Common/URI/file.pm blib/lib/Regexp/Common/URI/file.pm 
 cp lib/Regexp/Common/zip.pm blib/lib/Regexp/Common/zip.pm 
 cp lib/Regexp/Common/number.pm blib/lib/Regexp/Common/number.pm 
 cp lib/Regexp/Common/delimited.pm blib/lib/Regexp/Common/delimited.pm 
 cp lib/Regexp/Common/URI/RFC1808.pm blib/lib/Regexp/Common/URI/RFC1808.pm 
 cp lib/Regexp/Common/URI/wais.pm blib/lib/Regexp/Common/URI/wais.pm 
 cp lib/Regexp/Common/URI/tv.pm blib/lib/Regexp/Common/URI/tv.pm 
 cp lib/Regexp/Common/URI/http.pm blib/lib/Regexp/Common/URI/http.pm 
 cp lib/Regexp/Common/lingua.pm blib/lib/Regexp/Common/lingua.pm 
 cp lib/Regexp/Common/URI/fax.pm blib/lib/Regexp/Common/URI/fax.pm 
 cp lib/Regexp/Common/net.pm blib/lib/Regexp/Common/net.pm 
 cp lib/Regexp/Common/SEN.pm blib/lib/Regexp/Common/SEN.pm 
 cp lib/Regexp/Common/URI/gopher.pm blib/lib/Regexp/Common/URI/gopher.pm 
 cp lib/Regexp/Common/URI/pop.pm blib/lib/Regexp/Common/URI/pop.pm 
 Manifying blib/man3/Regexp::Common::URI::news.3pm 
 Manifying blib/man3/Regexp::Common::_support.3pm 
 Manifying blib/man3/Regexp::Common::balanced.3pm 
 Manifying blib/man3/Regexp::Common::comment.3pm 
 Manifying blib/man3/Regexp::Common::URI::telnet.3pm 
 Manifying blib/man3/Regexp::Common::URI::RFC2396.3pm 
 Manifying blib/man3/Regexp::Common::URI::tel.3pm 
 Manifying blib/man3/Regexp::Common::URI::RFC1738.3pm 
 Manifying blib/man3/Regexp::Common::CC.3pm 
 Manifying blib/man3/Regexp::Common::URI::RFC2384.3pm 
 Manifying blib/man3/Regexp::Common::URI::prospero.3pm 
 Manifying blib/man3/Regexp::Common::list.3pm 
 Manifying blib/man3/Regexp::Common::number.3pm 
 Manifying blib/man3/Regexp::Common::zip.3pm 
 Manifying blib/man3/Regexp::Common::URI::file.3pm 
 Manifying blib/man3/Regexp::Common::URI::RFC1808.3pm 
 Manifying blib/man3/Regexp::Common::URI::tv.3pm 
 Manifying blib/man3/Regexp::Common::URI::wais.3pm 
 Manifying blib/man3/Regexp::Common::URI::pop.3pm 
 Manifying blib/man3/Regexp::Common::URI::gopher.3pm 
 Manifying blib/man3/Regexp::Common::SEN.3pm 
 Manifying blib/man3/Regexp::Common::URI::ftp.3pm 
 Manifying blib/man3/Regexp::Common::whitespace.3pm 
 Manifying blib/man3/Regexp::Common::URI::RFC1035.3pm 
 Manifying blib/man3/Regexp::Common::profanity.3pm 
 Manifying blib/man3/Regexp::Common::URI.3pm 
 Manifying blib/man3/Regexp::Common::URI::RFC2806.3pm 
 Manifying blib/man3/Regexp::Common.3pm 
 Manifying blib/man3/Regexp::Common::delimited.3pm 
 Manifying blib/man3/Regexp::Common::URI::http.3pm 
 Manifying blib/man3/Regexp::Common::lingua.3pm 
 Manifying blib/man3/Regexp::Common::URI::fax.3pm 
 Manifying blib/man3/Regexp::Common::net.3pm 
   ABIGAIL/Regexp-Common-2011041701.tar.gz 
   /usr/bin/make -- OK 
 Warning (usually harmless): 'YAML' not installed, will not store persistent state 
 Running make test 
 PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t t/*/*.t 
 t/comment/delimited.t ............ ok          
 t/comment/html.t ................. ok          
 t/comment/nested.t ............... ok          
 t/comment/single_line.t .......... ok            
 t/comment/single_or_multiline.t .. ok          
 t/number/decimal.t ............... ok          
 t/number/integer.t ............... ok            
 t/number/number.t ................ ok      
 t/SEN/usa_ssn.t .................. ok          
 t/test___luhn.t .................. ok        
 t/test_balanced.t ................ ok        
 t/test_bases.t ................... ok        
 t/test_bases_sep.t ............... ok        
 t/test_comments.t ................ ok        
 t/test_curry.t ................... ok      
 t/test_delimited.t ............... ok      
 t/test_domain.t .................. ok      
 t/test_i.t ....................... ok      
 t/test_ip.t ...................... ok      
 t/test_keep.t .................... ok      
 t/test_lingua_palindrome.t ....... ok          
 t/test_list.t .................... ok      
 t/test_mac.t ..................... ok      
 t/test_no_import.t ............... ok    
 t/test_profanity.t ............... ok        
 t/test_roman.t ................... ok            
 t/test_squares.t ................. ok          
 t/test_sub.t ..................... ok      
 t/test_sub_named.t ............... ok    
 t/test_ws.t ...................... ok      
 t/URI/any.t ...................... ok      
 t/URI/fax.t ...................... ok      
 t/URI/file.t ..................... ok        
 t/URI/ftp.t ...................... ok        
 t/URI/gopher.t ................... ok            
 t/URI/http.t ..................... ok            
 t/URI/news.t ..................... ok        
 t/URI/nntp.t ..................... ok          
 t/URI/pop.t ...................... ok        
 t/URI/prospero.t ................. ok          
 t/URI/tel.t ...................... ok      
 t/URI/telnet.t ................... ok          
 t/URI/tv.t ....................... ok      
 t/URI/wais.t ..................... ok          
 t/zip/australia.t ................ ok          
 t/zip/belgium.t .................. ok          
 t/zip/denmark.t .................. ok          
 t/zip/france.t ................... ok          
 t/zip/germany.t .................. ok          
 t/zip/greenland.t ................ ok        
 t/zip/italy.t .................... ok          
 t/zip/netherlands.t .............. ok          
 t/zip/norway.t ................... ok          
 t/zip/spain.t .................... ok          
 t/zip/us.t ....................... ok          
 t/zip/zip.t ...................... ok      
 t/zzz_50_pod.t ................... skipped: Test::Pod required for testing POD 
 t/zzz_60_pod_coverage.t .......... skipped: Test::Pod::Coverage required for testing POD coverage 
 All tests successful. 
 Files=58, Tests=229047, 28 wallclock secs (21.70 usr  0.24 sys + 19.55 cusr  0.42 csys = 41.91 CPU) 
 Result: PASS 
   ABIGAIL/Regexp-Common-2011041701.tar.gz 
   /usr/bin/make test -- OK 
 Warning (usually harmless): 'YAML' not installed, will not store persistent state 
 Running make install 
 Prepending /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/arch /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/lib to PERL5LIB for 'install' 
 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
 ERROR: Can't create '/usr/local/man/man3' 
 mkdir /usr/local/man/man3: Permission denied at /usr/share/perl/5.10/ExtUtils/Install.pm line 483 
  
 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
  at -e line 1 
 make: *** [pure_site_install] Error 13 
   ABIGAIL/Regexp-Common-2011041701.tar.gz 
   /usr/bin/make install  -- NOT OK 
 Warning (usually harmless): 'YAML' not installed, will not store persistent state 
 Running install for module 'Text::CSV' 
 'YAML' not installed, falling back to Data::Dumper and Storable to read prefs '/home/ar/.cpan/prefs' 
 Running make for M/MA/MAKAMAKA/Text-CSV-1.21.tar.gz 
 Prepending /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/arch /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/lib to PERL5LIB for 'get' 
 Checksum for /home/ar/.cpan/sources/authors/id/M/MA/MAKAMAKA/Text-CSV-1.21.tar.gz ok 
 Text-CSV-1.21/ 
 Text-CSV-1.21/lib/ 
 Text-CSV-1.21/lib/Text/ 
 Text-CSV-1.21/lib/Text/CSV.pm 
 Text-CSV-1.21/lib/Text/CSV_PP.pm 
 Text-CSV-1.21/Makefile.PL 
 Text-CSV-1.21/files/ 
 Text-CSV-1.21/files/utf8.csv 
 Text-CSV-1.21/files/macosx.csv 
 Text-CSV-1.21/README 
 Text-CSV-1.21/t/ 
 Text-CSV-1.21/t/75_hashref.t 
 Text-CSV-1.21/t/41_null.t 
 Text-CSV-1.21/t/77_getall.t 
 Text-CSV-1.21/t/15_flags.t 
 Text-CSV-1.21/t/46_eol_si.t 
 Text-CSV-1.21/t/20_file.t 
 Text-CSV-1.21/t/45_eol.t 
 Text-CSV-1.21/t/00_pod.t 
 Text-CSV-1.21/t/10_base.t 
 Text-CSV-1.21/t/21_lexicalio.t 
 Text-CSV-1.21/t/30_types.t 
 Text-CSV-1.21/t/65_allow.t 
 Text-CSV-1.21/t/80_diag.t 
 Text-CSV-1.21/t/util.pl 
 Text-CSV-1.21/t/40_misc.t 
 Text-CSV-1.21/t/81_subclass.t 
 Text-CSV-1.21/t/55_combi.t 
 Text-CSV-1.21/t/22_scalario.t 
 Text-CSV-1.21/t/50_utf8.t 
 Text-CSV-1.21/t/71_pp.t 
 Text-CSV-1.21/t/51_utf8.t 
 Text-CSV-1.21/t/12_acc.t 
 Text-CSV-1.21/t/76_magic.t 
 Text-CSV-1.21/t/70_rt.t 
 Text-CSV-1.21/t/60_samples.t 
 Text-CSV-1.21/MANIFEST 
 Text-CSV-1.21/META.yml 
 Text-CSV-1.21/Changes 
 Prepending /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/arch /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/lib to PERL5LIB for 'make' 
  
   CPAN.pm: Going to build M/MA/MAKAMAKA/Text-CSV-1.21.tar.gz 
  
 Welcome to Text::CSV (v.1.21) 
 ============================= 
 If you install Text::CSV_XS v.0.80, it makes Text::CSV faster. 
  
 Checking if your kit is complete... 
 Looks good 
 Writing Makefile for Text::CSV 
 Could not read '/home/ar/.cpan/build/Text-CSV-1.21-vXHaNb/META.yml'. Falling back to other methods to determine prerequisites 
 cp lib/Text/CSV_PP.pm blib/lib/Text/CSV_PP.pm 
 cp lib/Text/CSV.pm blib/lib/Text/CSV.pm 
 Manifying blib/man3/Text::CSV_PP.3pm 
 Manifying blib/man3/Text::CSV.3pm 
   MAKAMAKA/Text-CSV-1.21.tar.gz 
   /usr/bin/make -- OK 
 Warning (usually harmless): 'YAML' not installed, will not store persistent state 
 Prepending /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/arch /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/lib to PERL5LIB for 'test' 
 Running make test 
 PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t 
 t/00_pod.t ........ skipped: Test::Pod 1.00 required for testing POD 
 t/10_base.t ....... ok      
 t/12_acc.t ........ ok        
 t/15_flags.t ...... ok        
 t/20_file.t ....... ok        
 t/21_lexicalio.t .. ok        
 t/22_scalario.t ... ok        
 t/30_types.t ...... ok      
 t/40_misc.t ....... ok      
 t/41_null.t ....... ok        
 t/45_eol.t ........ ok          
 t/46_eol_si.t ..... ok        
 t/50_utf8.t ....... ok      
 t/51_utf8.t ....... ok      
 t/55_combi.t ...... ok          
 t/60_samples.t .... ok    
 t/65_allow.t ...... ok          
 t/70_rt.t ......... ok        
 t/71_pp.t ......... ok      
 t/75_hashref.t .... ok      
 t/76_magic.t ...... ok    
 t/77_getall.t ..... ok      
 t/80_diag.t ....... ok        
 t/81_subclass.t ... ok    
 All tests successful. 
 Files=24, Tests=13588,  5 wallclock secs ( 1.71 usr  0.14 sys +  3.70 cusr  0.22 csys =  5.77 CPU) 
 Result: PASS 
   MAKAMAKA/Text-CSV-1.21.tar.gz 
   /usr/bin/make test -- OK 
 Warning (usually harmless): 'YAML' not installed, will not store persistent state 
 Running make install 
 Prepending /home/ar/.cpan/build/Text-CSV-1.21-vXHaNb/blib/arch /home/ar/.cpan/build/Text-CSV-1.21-vXHaNb/blib/lib /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/arch /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/lib to PERL5LIB for 'install' 
 Manifying blib/man3/Text::CSV_PP.3pm 
 Manifying blib/man3/Text::CSV.3pm 
 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
 ERROR: Can't create '/usr/local/man/man3' 
 mkdir /usr/local/man/man3: Permission denied at /usr/share/perl/5.10/ExtUtils/Install.pm line 483 
  
 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
  at -e line 1 
 make: *** [pure_site_install] Error 13 
   MAKAMAKA/Text-CSV-1.21.tar.gz 
   /usr/bin/make install  -- NOT OK 
 Warning (usually harmless): 'YAML' not installed, will not store persistent state 
 Running make for M/MS/MSISK/Finance-QuoteHist-1.16.tar.gz 
 Prepending /home/ar/.cpan/build/Text-CSV-1.21-vXHaNb/blib/arch /home/ar/.cpan/build/Text-CSV-1.21-vXHaNb/blib/lib /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/arch /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/lib to PERL5LIB for 'get' 
   Has already been unwrapped into directory /home/ar/.cpan/build/Finance-QuoteHist-1.16-CDmEVD 
 Prepending /home/ar/.cpan/build/Text-CSV-1.21-vXHaNb/blib/arch /home/ar/.cpan/build/Text-CSV-1.21-vXHaNb/blib/lib /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/arch /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/lib to PERL5LIB for 'make' 
  
   CPAN.pm: Going to build M/MS/MSISK/Finance-QuoteHist-1.16.tar.gz 
  
 cp lib/Finance/QuoteHist/Generic.pm blib/lib/Finance/QuoteHist/Generic.pm 
 cp lib/Finance/QuoteHist/Yahoo/Australia.pm blib/lib/Finance/QuoteHist/Yahoo/Australia.pm 
 cp lib/Finance/QuoteHist/BusinessWeek.pm blib/lib/Finance/QuoteHist/BusinessWeek.pm 
 cp lib/Finance/QuoteHist/QuoteMedia.pm blib/lib/Finance/QuoteHist/QuoteMedia.pm 
 cp lib/Finance/QuoteHist.pm blib/lib/Finance/QuoteHist.pm 
 cp lib/Finance/QuoteHist/Google.pm blib/lib/Finance/QuoteHist/Google.pm 
 cp lib/Finance/QuoteHist/Yahoo.pm blib/lib/Finance/QuoteHist/Yahoo.pm 
 cp lib/Finance/QuoteHist/StockNod.pm blib/lib/Finance/QuoteHist/StockNod.pm 
 cp lib/Finance/QuoteHist/Investopedia.pm blib/lib/Finance/QuoteHist/Investopedia.pm 
 cp lib/Finance/QuoteHist/MSN.pm blib/lib/Finance/QuoteHist/MSN.pm 
 Manifying blib/man3/Finance::QuoteHist::Generic.3pm 
 Manifying blib/man3/Finance::QuoteHist::Yahoo::Australia.3pm 
 Manifying blib/man3/Finance::QuoteHist::BusinessWeek.3pm 
 Manifying blib/man3/Finance::QuoteHist::QuoteMedia.3pm 
 Manifying blib/man3/Finance::QuoteHist.3pm 
 Manifying blib/man3/Finance::QuoteHist::Google.3pm 
 Manifying blib/man3/Finance::QuoteHist::Investopedia.3pm 
 Manifying blib/man3/Finance::QuoteHist::Yahoo.3pm 
 Manifying blib/man3/Finance::QuoteHist::StockNod.3pm 
 Manifying blib/man3/Finance::QuoteHist::MSN.3pm 
   MSISK/Finance-QuoteHist-1.16.tar.gz 
   /usr/bin/make -- OK 
 Warning (usually harmless): 'YAML' not installed, will not store persistent state 
 Prepending /home/ar/.cpan/build/Text-CSV-1.21-vXHaNb/blib/arch /home/ar/.cpan/build/Text-CSV-1.21-vXHaNb/blib/lib /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/arch /home/ar/.cpan/build/Regexp-Common-2011041701-SPtu61/blib/lib to PERL5LIB for 'test' 
 Running make test 
 PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t 
 t/00_basic.t ...... ok    
 t/05_csv.t ........ ok        
 t/10_quotes.t ..... ok      
 t/20_dividends.t .. ok    
 t/30_splits.t ..... 1/6 WARNING: Could not fetch split for some symbols (CPKI). Abandoning request for these symbols. Don't worry, though, we were looking for splits. These are less likely to exist compared to quotes. 
 t/30_splits.t ..... 5/6  
 #   Failed test 'direct split (yahoo) (rows)' 
 #   at t/30_splits.t line 35. 
 #          got: 0 
 #     expected: 1 
  
 #   Failed test 'direct split (yahoo) (content)' 
 #   at t/30_splits.t line 39. 
 #     Structures begin differing at: 
 #          $got->[0] = Does not exist 
 #     $expected->[0] = 'CPKI:2007/06/19:3:2' 
 # Looks like you failed 2 tests of 6. 
 t/30_splits.t ..... Dubious, test returned 2 (wstat 512, 0x200) 
 Failed 2/6 subtests  
     (less 4 skipped subtests: 0 okay) 
  
 Test Summary Report 
 ------------------- 
 t/30_splits.t   (Wstat: 512 Tests: 6 Failed: 2) 
   Failed tests:  5-6 
   Non-zero exit status: 2 
 Files=5, Tests=210,  4 wallclock secs ( 0.05 usr  0.02 sys +  1.35 cusr  0.09 csys =  1.51 CPU) 
 Result: FAIL 
 Failed 1/5 test programs. 2/210 subtests failed. 
 make: *** [test_dynamic] Error 2 
   MSISK/Finance-QuoteHist-1.16.tar.gz 
   /usr/bin/make test -- NOT OK 
 //hint// to see the cpan-testers results for installing this module, try: 
   reports MSISK/Finance-QuoteHist-1.16.tar.gz 
 Warning (usually harmless): 'YAML' not installed, will not store persistent state 
 Running make install 
   make test had returned bad status, won't install without force 
 Failed during this command: 
  ABIGAIL/Regexp-Common-2011041701.tar.gz      : install NO 
  MAKAMAKA/Text-CSV-1.21.tar.gz                : install NO 
  MSISK/Finance-QuoteHist-1.16.tar.gz          : make_test NO 
 
```

that's why when I run my perl program, I get the following error:
```

Can't locate Finance/QuoteHist.pm in @INC

```

---

### Post by blueridgedog on 2011-07-25
It looks like it copied it:

```
cp lib/Finance/QuoteHist/Generic.pm blib/lib/Finance/QuoteHist/Generic.pm 
```

How are you calling it in your script?

---

### Post by itba on 2011-07-25
this is my script.
```

#!/usr/bin/perl -w
use strict;
use Finance::QuoteHist;

$q= Finance::QuoteHist->new
(
symbols =>[qw(MCO EXPE)],
start_date => '01/01/2000',
 end_date => 'today',
);

print "quotes\n";

foreach $row($q->quotes())
{
($date, $open, $high, $low, $close, $volume) = @$row;
print "$date $close\n";
}

@dividends = $q->dividends();
if(@dividends)
{
    print "\nDividends\n";
foreach $row ($q->dividends())
{
($date, $amount) = @$row;
print "$date $amount\n";
}
}

```

---

### Post by dethorpe on 2011-07-25
Cpan is failing to install the pre-requisite package due to permission denied error. 
 
```
ERROR: Can't create '/usr/local/man/man3' 
mkdir /usr/local/man/man3: Permission denied at /usr/share/perl/5.10/ExtUtils/Install.pm line 483 
 
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
  at -e line 1 
make: *** [pure_site_install] Error 13 

``` 
 
Your user probably dosn't have write access to the system perl or man directories so need to run cpan as root using "sudo cpan" in order to install to the system perl directory.

---

### Post by itba on 2011-07-25
so, I ran cpan using sudo cpan, and then the install Finance::QuoteHist

and I can post the entire message, but these are the test statistics towards the end of the run:

```

Test Summary Report
-------------------
t/30_splits.t   (Wstat: 512 Tests: 6 Failed: 2)
  Failed tests:  5-6
  Non-zero exit status: 2
Files=5, Tests=210,  3 wallclock secs ( 0.05 usr  0.01 sys +  1.30 cusr  0.08 csys =  1.44 CPU)
Result: FAIL
Failed 1/5 test programs. 2/210 subtests failed.
make: *** [test_dynamic] Error 2
  MSISK/Finance-QuoteHist-1.16.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports MSISK/Finance-QuoteHist-1.16.tar.gz
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make install
  make test had returned bad status, won't install without force
Failed during this command:
 MSISK/Finance-QuoteHist-1.16.tar.gz          : make_test NO

```

---

### Post by itba on 2011-07-25
I downloaded the module from the author's page and figured I'd change my script to tell @INC to include the module:
```

#!/usr/bin/perl -w
use strict;
use lib "/home/ar/Finance-QuoteHist-1.16/lib";
use Finance::QuoteHist;

```and now I get the following compilation errors:
```

Global symbol "$q" requires explicit package name at hist.pl line 7.
Global symbol "$row" requires explicit package name at hist.pl line 15.
Global symbol "$q" requires explicit package name at hist.pl line 15.
Global symbol "$date" requires explicit package name at hist.pl line 17.
Global symbol "$open" requires explicit package name at hist.pl line 17.
Global symbol "$high" requires explicit package name at hist.pl line 17.
Global symbol "$low" requires explicit package name at hist.pl line 17.
Global symbol "$close" requires explicit package name at hist.pl line 17.
Global symbol "$volume" requires explicit package name at hist.pl line 17.
Global symbol "$row" requires explicit package name at hist.pl line 17.
Global symbol "$date" requires explicit package name at hist.pl line 18.
Global symbol "$close" requires explicit package name at hist.pl line 18.
Global symbol "@dividends" requires explicit package name at hist.pl line 21.
Global symbol "$q" requires explicit package name at hist.pl line 21.
Global symbol "@dividends" requires explicit package name at hist.pl line 22.
Global symbol "$row" requires explicit package name at hist.pl line 25.
Global symbol "$q" requires explicit package name at hist.pl line 25.
Global symbol "$date" requires explicit package name at hist.pl line 27.
Global symbol "$amount" requires explicit package name at hist.pl line 27.
Global symbol "$row" requires explicit package name at hist.pl line 27.
Global symbol "$date" requires explicit package name at hist.pl line 28.
Global symbol "$amount" requires explicit package name at hist.pl line 28.
Execution of hist.pl aborted due to compilation errors.

```any suggestions on how I can fix this...if this is the only way to get it to work

---

### Post by dethorpe on 2011-07-26
Its failing some tests so dosen't install. 
 
I don't know the module but looking at the error seems it can't find something Yahoo related. 
 
```
 
 t/30_splits.t ..... 1/6 WARNING: Could not fetch split for some symbols (CPKI). Abandoning request for these symbols. Don't worry, though, we were looking for splits. These are less likely to exist compared to quotes. 
t/30_splits.t ..... 5/6  
#   Failed test 'direct split (yahoo) (rows)' 
#   at t/30_splits.t line 35. 
#          got: 0 
#     expected: 1 
 
#   Failed test 'direct split (yahoo) (content)' 
#   at t/30_splits.t line 39. 
#     Structures begin differing at: 
#          $got->[0] = Does not exist 
#[COLOR=red]     $expected->[0] = 'CPKI:2007/06/19:3:2' [/COLOR]
# Looks like you failed 2 tests of 6. 
t/30_splits.t ..... Dubious, test returned 2 (wstat 512, 0x200) 
Failed 2/6 subtests  
     (less 4 skipped subtests: 0 okay) 
 

```
 
This might be OK (e.g. if CPKI dosn't exist any more on yahoo) or a problem in the test itself so you can try to force the install using the force option in cpan. If you do that and then get odd errors when using the module it may mean there is actually a problem in the module install.
 
The errors you show are in your script, when using "strict" (which is good) you have to declare all variables with "my" other wise you get the error shown . e.g.:
 
```
 
my $q= Finance::QuoteHist->new
 
foreach my $row ($q->quotes())
 

```
 
Be worth reading up on "my" to understand the reasons for this. ([http://perldoc.perl.org/functions/my.html](http://perldoc.perl.org/functions/my.html))

---

### Post by itba on 2011-07-26
thanks for the link....will check it out.
CPKI symbol has been changed, but you mentioned "you can try to force the install using the force option in cpan"....how do I do that?
Also, is it true that using the system perl that comes with ubuntu creates problems for permissions to the /etc/perl directory....is there a fix around that...using sudo doesn't seem to help when it comes to accessing the directories where @INC looks...

---

### Post by dethorpe on 2011-07-28
Just preceed the command with "force" 
 
```
 
force install Finance::QuoteHist 

```
 
Should be able to access /etc/perl with sudo fine. What particuler problem are you encountering?
 
Note: Its sometimes worth (but not essential) installing a seperate perl installation to use for your own scripts and development, Can then install any extra modules to that using cpan. This removes any chance of damaging the system perl installation with your own modules or cpan installed ones, especially if you need different versions to the standard system perl modules. 
 
Check out "perlbrew" as an easy way to do this and switch between different perls installed in your home directory, so all cpan libs are also insalled there so no sudo required.
 
[http://search.cpan.org/~gugod/App-perlbrew/lib/App/perlbrew.pm](http://search.cpan.org/~gugod/App-perlbrew/lib/App/perlbrew.pm)

---

### Post by itba on 2011-07-29
thanks dethorpe
the force install worked smooth :)

to your point re. a separate perl installation, I actually installed ActivePerl the other day in my home directory, but everytime I run a perl -V, it shows me the system perl v. 5.10....
I will check out perlbrew, maybe that has the answer to how I can switch to ActivePerl.

---

