---
title: "convert a byte sequence to an image in gtk+"
date: 2011-07-07
forum: General Help
---

### Post by rahulagr2000 on 2011-07-07
Hi,
I'm working on image acquisition from an IP camera(axis) -accessing network using gnet library.
I am receiving a byte sequence in a gchar * pointer...Now, I want to convert this to an image so that i can use it to process in openCV .. 
My code is as follows.. i am completely new to these libraries..please help me with this

/////////////////////////////////////////////////////

#define GNET_EXPERIMENTAL
#include <gnet.h>
#include <stdio.h>
#include <conn-http.h>
#include <opencv/highgui.h>
#include <opencv/cxcore.h>
#include <opencv/cv.h>
//#include <gio/gio.h>
#include <gtk/gtk.h>



int main(int argc, char ** argv)
{
  struct GtkWidget *image;
  GConnHttp  *conn;
  
  conn = gnet_conn_http_new();
  
  gnet_conn_http_set_uri(conn, "http://10.64.260.30/axis-cgi/jpg/image.cgi");
    if (gnet_conn_http_run(conn, NULL, NULL))
  {
    gchar *buf;
    gsize  buflen;
    if (gnet_conn_http_steal_buffer(conn, &buf, &buflen))
    {
      g_print ("Received %u bytes of data:\n", buflen);

    image =  gtk_image_get_from_buf(&buf);
      
//printf("size of buf is %d",sizeof(buf));      
      
          /////////opencv
      
      IplImage* img = cvLoadImage( image, 1 );
      cvShowImage("MAGIC",img);
      while( 1 ) 
    {
          if( cvWaitKey( 100 ) == 27 ) break;
          }
      cvReleaseImage( &img );

    exit(0);
    return 0;
    }
  }
 gnet_conn_http_delete(conn);
}

////////////////////////////////////////////////////////////////////////////////////

thanks

---

