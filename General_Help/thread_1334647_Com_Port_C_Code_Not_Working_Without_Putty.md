---
title: "Com Port C Code Not Working Without Putty?"
date: 2009-11-22
forum: General Help
---

### Post by Nekativ on 2009-11-22
Well I am not totally sure where to post this question since it seems to be a weird one, but here it goes.

We wrote some C code to send the digit "1" through ttyUSB1. It works, however it only works while Putty has that particular port open.

I would assume that we need to somehow configure the script to open the com port, and putty somehow is opening the com port and setting the BAUD rate for us, but honestly I am not totally sure and I cannot seem to find a way to do this. 

The code we have written so far sends '1' through ttyUSB1 and then 10 second later sends 'q' through ttyUSB1:

```
#include <stdio.h>

#include <string.h>

#include <fcntl.h>

#include <errno.h>

#include <termios.h>

#include <unistd.h>

int fd1;

int fd2;

char tempchar = '1';
const void* buf = &tempchar;

char tempcharq = 'q';
const void* bufq = &tempcharq;



char *buff,*buffer,*bufptr;

int wr,rd,nbytes,tries;

int main()
{
    fd1=open("/dev/ttyUSB1", O_RDWR | O_NOCTTY | O_NDELAY);

    if (fd1 == -1 )
    {
        perror("open_port: Unable to open /dev/ttyUSB1 – ");
    }

    else
    {
        fcntl(fd1, F_SETFL,0);
        printf("Port has been sucessfully opened and %d is the file description\n",fd1);
    }


    wr=write(fd1, buf, 1);

        sleep(10);

    wr=write(fd1, bufq, 1);

    //wr=write(fd1, "ATZ\r",4);

    //rd=read(fd1,buff,1);

    //printf("bytes sent are %d \n", rd);

    close(fd1);


    return 0;
}
```Any help will be rewarded with forum popcorn or a star, it's really of your choosing :P

---

### Post by Nekativ on 2009-11-22
bump

---

### Post by Nekativ on 2009-11-29
bump

---

