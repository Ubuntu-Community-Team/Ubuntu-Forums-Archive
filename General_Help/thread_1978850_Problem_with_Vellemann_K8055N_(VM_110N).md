---
title: "Problem with Vellemann K8055N (VM 110N)"
date: 2012-05-12
forum: General Help
---

### Post by uranusnucleus on 2012-05-12
Hello to everyone,

I have a problem with the (new) Experiment Interface Board VM 110N / K8055N. Well, the old interface Board VM110 K8055 works fine (user rights, driver [[http://libk8055.sourceforge.net/]](http://libk8055.sourceforge.net/])), but now the new board does not work. Does anyone have similar problems? Or better does anyone have a solution?

With[INDENT]sudo lsusb -v 
[/INDENT]I got "nearly" the same results. Nearly at this place means there is a difference in the USB version old=usb1.1, new=usb2.0.
The vendor string and the product string are the same.
When I run the k8055 program it also connects, but when the program try to read it tells 3 times "Read retry" ...

uranus@i7-2600:~/PROJEKTE/Velleman-K8055/src$ sudo ./k8055 -debug
Parameters : Card=0 Analog1=-1 Analog2=-1 Digital=-1
Velleman Device Found @ Address 004 Vendor 0x010cf Product ID 0x05500
Got driver name: usbhid
Disconnected OS driver: No error
Found interface 0
Took over the device
Read retry
Read retry
Read retry
Could not open the k8055 (port:0)
Please ensure that the device is correctly connected.

Does anyone have an idea?
Uranus Nucleus

---

### Post by 3dot14User on 2012-10-23
Hello Uranusnucleus,

Sorry for the late reply.

Unfortunatley I'm facing the same problem.
Did you found a solution in between?

I want to use the board with a raspberry pi and domotiga because the old board isn't available any more.

Thanks for a short reply even if you can tell me that it doesn't work.

Regards
3dot14user

---

### Post by 3dot14User on 2012-10-25
Hi Uranus Nucleus,
I found your post on the Vellemann support foruk for the VM110N.
Thanks alot.

For all others please found what I did based on Uranus solution:

(search the Vellemann forum for VM110N and linux)

Just  add one line to k8055.c (see below the one with +10), make, make  install and the N-2 board is running (assuming that you have installed  libusb etc.)

/* Actual read of data from the device endpoint, retry 3 times if not responding ok */
static int ReadK8055Data(void)
{
    int read_status = 0, i = 0;

    if (CurrDev->DevNo == 0) return K8055_ERROR;

    for(i=0; i < 3; i++)
        {
       read_status = usb_interrupt_read(CurrDev->device_handle,  USB_INP_EP, (char *)CurrDev->data_in, PACKET_LEN, USB_TIMEOUT);
         if ((read_status == PACKET_LEN) && (CurrDev->data_in[1]  == CurrDev->DevNo )) return 0; /* works with K8055 / VM110 */
         if ((read_status == PACKET_LEN) && (CurrDev->data_in[1]  == CurrDev->DevNo +10)) return 0; /* works with K8055N / VM110N */

        if (DEBUG)
            fprintf(stderr, "Read retry\n");
        }
    return K8055_ERROR;
}
 I had to perform a sudo ldconfig to run domotiga (lib not found issue)
Regards,
3dot14User

---

