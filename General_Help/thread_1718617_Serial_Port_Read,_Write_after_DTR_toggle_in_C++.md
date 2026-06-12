---
title: "Serial Port Read, Write after DTR toggle in C++"
date: 2011-03-31
forum: General Help
---

### Post by TPWT on 2011-03-31
Hi all

I need to read and write to a serial device. When I connect via gtkterm, I need to toggle DTR before I can communicate with the device .

My problem is that I cannot emulate this in C++.

I want to write some code that can setup a comport, toggle the DTR, then read and write strings to the port. However all my attempts have been fruitless.

My serial settings are B9600, No parity, no hardware control, 8 bt characters and 1 stop bit:

```

#include <iostream>
#include <SerialStream.h>
#include <sys/ioctl.h>
#include <fcntl.h>
using namespace LibSerial;
using namespace std;



int main()

{
    char byte;

        //connect to ttyUSB0
        SerialPort mySerialPort("/dev/ttyUSB0");

        //open
        mySerialPort.Open(SerialPort::BAUD_9600, SerialPort::CHAR_SIZE_8, SerialPort::PARITY_NONE, SerialPort::STOP_BITS_1, SerialPort::FLOW_CONTROL_NONE);

/*
        int fd;
        fd=open("/dev/ttysUSB0",O_RDWR||O_NONBLOCK);
//        struct termios ComParams

        int iFlags;
        iFlags=TIOCM_DTR;
        ioctl(fd,TIOCMBIC,&iFlags);
*/



while(1){
        cout << "In" << endl;

        //read with a timeout of 500 ms
        byte = mySerialPort.ReadByte(10000);

        cout << byte << endl;

/*
        cout << "Out" << endl;
        //write a byte
        mySerialPort.WriteByte(0xbfb9694c);
*/

        //cout << "Done" << endl;
}

        //close port
    //    mySerialPort.Close();

        cout << "Closed" << endl;

    return 0;
}

```

---

### Post by wt8008 on 2011-04-01
It seems like you are using LibSerial to perform the IO. I do not know C++, but since no one answered you so far, I can share this link: [http://www.easysw.com/~mike/serial/serial.html#5_1_1](http://www.easysw.com/~mike/serial/serial.html#5_1_1)

See the `Setting the Control Signals' section, maybe it can help you for what you need to search for.

---

