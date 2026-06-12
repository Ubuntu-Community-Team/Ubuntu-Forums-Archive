---
title: "Problem reading serial port"
date: 2010-05-23
forum: General Help
---

### Post by tanmayiit on 2010-05-23
Hi,
I am using a F232 USB to serial adapter for connecting my wireless modem to my laptop and I wrote a simple C code for reading data received by the modem transmitted by another modem installed on my target device.The problem is my code is simply giving 0.00000 (float data) output .When I use the same code with my desktop its running fine and I am getting relevant data.What may be the problem? I even changed the permission for my /dev/ttyUSB0 

I am using Ubuntu 10.04 on both my laptop and desktop

below is my code

```

#include <stdlib.h>
#include <math.h>
#include <errno.h>   /* Error number definitions */
#include <termios.h> /* POSIX terminal control definitions */
#include <unistd.h>  /* UNIX standard function definitions */
#include <fcntl.h>   /* File control definitions */
#include <stdio.h>

int openttyUSB(int);
int main(int argc,char **argv)
{
	
	float f;unsigned char c[9],d;int ttyfd;float D[2];	
	ttyfd = openttyUSB(0);	
  	if(ttyfd<0) 
		return -1;
  	f=2.;

	for(;;)	
	{
		read(ttyfd,&d,1);
		if(d==0xAA)
		{
			read(ttyfd,&c,9);
			if(c[0]==0xFF)
			{
				read(ttyfd,&c,8);
				D[0]=*(float*)&c[1];
				D[1]=*(float*)&c[5];
									
				printf("%f\t%f\n",D[0],D[1]);				
				

			}
		}
		
			
	}
  	return 0;
}

int openttyUSB(int port)
{
	int fd;
	fd=open("/dev/ttyUSB0", O_RDWR | O_NOCTTY | O_NDELAY);
	if(fd==-1)
	{
		perror("erreur"); 
		return -1;
	}			

	printf("File descriptor open : %d\n",fd);			
	struct termios options;						
   	tcgetattr(fd, &options);							
   	tcflush(fd, TCIFLUSH);								
    	options.c_cflag = B9600 | CS8 | CLOCAL | CREAD;	
	options.c_lflag = IGNPAR;							
	options.c_iflag = 0;								
   	options.c_oflag = 0;								
	options.c_cc[VTIME] = 0;
	if(tcsetattr(fd, TCSANOW, &options)==-1)
	{
		perror("erreur status"); 
		return -1;
	}
	return fd;
}

```

and the output I get on my laptop
```

File descriptor open :3
0.000000	0.000000
0.000000	0.000000
0.000000	0.000000
0.000000	0.000000
0.000000	0.000000
0.000000	0.000000
^C

```
whereas on my Desktop I get numerical values in float

---

### Post by damien_d on 2010-05-23
What's the target platform?

I remember from a looooong time ago some subtly when casting floats, depending on the FPU of the processor.

Also, check the endian-ness of your platform (which will help by stating the target)

```

				D[0]=*(float*)&c[1];
				D[1]=*(float*)&c[5];

```

Can you try something like:
```

float deserialise_float(uint8_t *array)
{
    union
    {
        uint8_t byData[4];
        float fData;
    } uData;

    for (unsigned int i = 0 ; i < sizeof(float) ; ++i)
        uData.byData[i] = array[i];

    return uData.fData;
}

```

---

### Post by damien_d on 2010-05-23
Here's another version, albeit in C++

```

uint32_t To_uint32_t(const std::vector<uint8_t> &array, unsigned int startIndex)
{
    if (array.size() >= startIndex + 4)
    {
        return   (static_cast<uint32_t>(array[startIndex + 3]) << 24) +
                 (static_cast<uint32_t>(array[startIndex + 2]) << 16) +
                 (static_cast<uint32_t>(array[startIndex + 1]) <<  8) +
                 (static_cast<uint32_t>(array[startIndex + 0])      );
    }

    // Something has gone wrong
    return 0;
}

float To_float(const std::vector<uint8_t> &inputData, unsigned int startIndex)
{

    float fData;
    uint32_t uiData;

    uiData = To_uint32_t(inputData, startIndex);

    __builtin_memcpy(&fData, &uiData, sizeof(fData));
    return fData;
}

```

This messy code works on production PPC and x86 platforms.  Hope it works for you - it's an easy exercise to translate to C-Based arrays.

  -- Damien

---

### Post by tanmayiit on 2010-05-27
thnx I will do the changes and post the results

---

### Post by tanmayiit on 2010-06-15
ok,I tried above two methods and still facing the same problem :confused:

---

### Post by damien_d on 2010-06-15
> **tanmayiit said:**
> ok,I tried above two methods and still facing the same problem :confused:

On your target device, can do do the following at the terminal:
```

stty -F /dev/ttyUSB0 115200 raw

```

(or whatever your baudrate happens to be).
 
Then, output the the following:
```

cat /dev/ttyUSB0 | hexdump -C

```

The values you get from hexdump that you think are floats, put into the following code:

```

// Not compiled! check for typos...
#include <stdio.h>

int main(void)
{
    // Put your values from hexdump here!
    uint8_t data[] = { VALUE_0, VALUE_1, VALUE_2, VALUE_3 };
    float converted;

    // This routine was supplied before, convert to C before use.
    converted = To_float(data, 0);

    // And let yourself know what the result was
    printf("0x%02X 0x%02X 0x%02X 0x%02X = %f\n",
        data[0], data[1], data[2], data[3], converted);

    return 0;
}

```

There is a good chance that the default serial port options change between one system and another.  It may be one of the differences that you're seeing.

  -- Damien

---

