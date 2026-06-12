---
title: "Stack Smashing"
date: 2010-06-16
forum: General Help
---

### Post by kemiko on 2010-06-16
I have a problem with "stack smashing" on Ubuntu 8.04 LTS.  I have read a bunch on this topic.  I fixed on other scenario, but this one I do not get.  I am porting from RedHat 7.0.  GDB output, function call and definition follow:


(gdb) where
#0  write_xml_log (type=0x80a188a "update", program=0x80a187d "edit_polpend", carrier=121, policy=618000, transaction=12) at editlog.c:11
#1  0x0804a60c in main (argc=Cannot access memory at address 0xc
) at edit_polpend.c:272
(gdb) finish
Run till exit from #0  write_xml_log (type=0x80a188a "update", program=0x80a187d "edit_polpend", carrier=121, policy=618000, transaction=12) at editlog.c:11
*** stack smashing detected ***: /data/prg/devprg/devel/astro/edit/edit_polpend terminated
...
Program received signal SIGABRT, Aborted.
0xb7fe3410 in __kernel_vsyscall ()



write_xml_log( "update", "edit_polpend", carrier_code, PendInstRec[index].PolNum, index + 1 );



write_xml_log( char *type, char *program, int carrier, int policy, int transaction )
{
  char buffer[101] = "";
  char *pbuffer = buffer;
  char filename[101] = "";
  FILE *fp;
  int newfile = 0;

  pbuffer += sprintf( pbuffer, " <%s", type );
  pbuffer += sprintf( pbuffer, " user=%c%-8s%c", '"', usr.unix_id, '"' );
  pbuffer += sprintf( pbuffer, " date=%c%d%02d%02d%c", '"', current_year1( ), current_month( ), current_day( ), '"' );
  pbuffer += sprintf( pbuffer, " time=%c%08d%c", '"', current_time( ), '"'  );
  pbuffer += sprintf( pbuffer, " carrier=%c%03d%c", '"', carrier, '"' );
  pbuffer += sprintf( pbuffer, " policy=%c%d%c", '"', policy, '"' );
  pbuffer += sprintf( pbuffer, " trans=%c%03d%c", '"', transaction, '"' );

  pbuffer += sprintf( pbuffer, " />\n" );

  sprintf( filename, "%s/%s.xml", __system_directory, program );

  fp = fopen( filename, "r" );
  if( fp )
  {
    fclose( fp );
  }
  else
  {
    newfile = 1;
  }

  fp = fopen( filename, "a" );
  if( newfile )
  {
    fprintf( fp, "<?xml version=\"1.0\"?>\n" );
    fprintf( fp, "<changelog>\n" );
  }
  fprintf( fp, "%s", buffer );
  fclose( fp );
}


Also why do I get "main (argc=Cannot access memory at address 0xc" in the stack???

---

### Post by john newbuntu on 2010-06-16
Perhaps a buffer overflow read/write on the "filename" array (or "buffer" array) that are on the stack.  You will have to step into the function to get more details.

The "argc=Cannot access memory" is probably because of compiler optimization although I could be wrong here.

---

### Post by kemiko on 2010-06-16
Solved, it was the buffer array by one stupid character!  SPE is always sooo nice.  Thanks a million.

---

