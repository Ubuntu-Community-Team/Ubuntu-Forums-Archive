---
title: "Ubuntu 8.04 LTS - 2GB file limit."
date: 2011-02-08
forum: General Help
---

### Post by kemiko on 2011-02-08
Hello,

I can use dd to write a 3GB file, but can not write a 3GB file with a C program.  Please see the following dd command and C program.

So, why can't C write over a 2GB file?  I have tried unbuffered and buffered C functions.

I am using ext3.

Thanks, Kent


15:26 root / > dd count=3 bs=1073741824 if=/dev/zero of=/tmp/3GB
3+0 records in
3+0 records out
3221225472 bytes (3.2 GB) copied, 53.6392 s, 60.1 MB/s


#include <stdio.h>

int main( int argc, char **argv )
{
  FILE *fp;
  long int i;

  fp = fopen( "/tmp/2GB", "w" );

  for( i = 0; i < 1073741824 ; i++ )
  {
    fprintf( fp, "000" );
  }
}

---

### Post by dcstar on 2011-02-08
> **kemiko said:**
> Hello,

I can use dd to write a 3GB file, but can not write a 3GB file with a C program.  Please see the following dd command and C program.

So, why can't C write over a 2GB file?  I have tried unbuffered and buffered C functions.

I am using ext3.

Thanks, Kent


15:26 root / > dd count=3 bs=1073741824 if=/dev/zero of=/tmp/3GB
3+0 records in
3+0 records out
3221225472 bytes (3.2 GB) copied, 53.6392 s, 60.1 MB/s


#include <stdio.h>

int main( int argc, char **argv )
{
  FILE *fp;
  long int i;

  fp = fopen( "/tmp/2GB", "w" );

  for( i = 0; i < 1073741824 ; i++ )
  {
    fprintf( fp, "000" );
  }
}

[LIST=1]
[*]Programming questions belong in the Programming forum
[*]Figure out the limits of a signed long int (which is probably what this school assignment is supposed to get **YOU** to figure out).
[/LIST]

---

