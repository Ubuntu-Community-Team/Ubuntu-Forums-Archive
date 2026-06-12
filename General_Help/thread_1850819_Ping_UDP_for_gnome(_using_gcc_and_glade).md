---
title: "Ping UDP for gnome( using gcc and glade)"
date: 2011-09-27
forum: General Help
---

### Post by ngubk on 2011-09-27
Hi there! I'm pretty much a newbie in making apps using glade and programming with gcc. I'm challenging myself by making a simple app to ping using UDP. But it still can't run( dunno why but it already cost me a day). Could you please look at it for me. Thanks a lot!

There are 4 files:

header.c
 ```
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<unistd.h>
#include<errno.h>
#include<sys/types.h>
#include<sys/socket.h>
#include<sys/time.h>
#include<netinet/in.h>
#include<arpa/inet.h>
#include<time.h>
#include  <netdb.h>
#include  <pthread.h>
#define PORTSERVER 6000 
#define PORTCLIENT 5000
 struct sockaddr_in  my_addr;
typedef struct UDP 
  {
    unsigned short stt;
    struct timeval time_stamp;
  }udp;
void message(char* txt);
void * start();
```

client.c
```
#include <gtk/gtk.h>
#include <glib.h>
#include <glib/gthread.h>
#include "header.h"
static GtkWidget *window;
static GtkWidget *ip;
static GtkWidget *port;
static GtkWidget *txtshow;
static GtkWidget *ping;
static GtkWidget *packet;
void on_ping_clicked();
void message(char* txt);
int main(int argc, char* argv[])
{
  
    gtk_init (&argc, &argv);
    GtkBuilder      *builder;
    builder = gtk_builder_new ();
    gtk_builder_add_from_file (builder, "form.xml", NULL);
    
    window = GTK_WIDGET (gtk_builder_get_object (builder, "window"));
    ip = GTK_WIDGET (gtk_builder_get_object (builder, "ip"));
    port = GTK_WIDGET (gtk_builder_get_object (builder, "port"));
    txtshow = GTK_WIDGET (gtk_builder_get_object (builder, "txtshow"));
    ping = GTK_WIDGET (gtk_builder_get_object (builder, "ping"));
    packet = GTK_WIDGET (gtk_builder_get_object (builder, "packet"));
        
    gtk_builder_connect_signals (builder, NULL);
    g_object_unref (G_OBJECT (builder));
    gtk_widget_show(window);
    
    //g_signal_connect(GTK_BUTTON(ping), "clicked",G_CALLBACK (start), NULL);

    gtk_main();
   
    return 0;
}

void message(char* txt)  //show message on widget: txtshow
{
	GtkTextIter start, end;
	GtkTextBuffer *buff;
	char* text = (char *)malloc (10000);
	buff = gtk_text_view_get_buffer (GTK_TEXT_VIEW (txtshow));
	gtk_text_buffer_get_start_iter (buff, &start);
	gtk_text_buffer_get_end_iter (buff, &end);
	strcpy(text, gtk_text_buffer_get_text(buff, &start, &end, TRUE));
	strcat(text, txt);
	gtk_text_buffer_set_text (buff, text,-1);
	gtk_widget_show(GTK_WIDGET(txtshow));
}


void on_ping_clicked()
{
  	int sockfd, rbytes ,i, n, sbytes,addrlen;
	char * result;
	char * result1;
	const gchar *ip_sv,*port_sv, *pk;

	pk = gtk_entry_get_text(GTK_ENTRY (packet));
	ip_sv = gtk_entry_get_text(GTK_ENTRY (ip));
	port_sv = gtk_entry_get_text(GTK_ENTRY (port));
	n= atoi(pk);
	udp Udp;
	char buf[1000];message("abc");// it doesn't show , dunno why
	struct sockaddr_in server_addr;
	struct sockaddr_in my_addr;
	server_addr.sin_family = AF_INET;
	if(port_sv == NULL) message("Please enter Port");
	else server_addr.sin_port = htons(atoi(port_sv));
       
        if(ip_sv == NULL) server_addr.sin_addr.s_addr = inet_addr("127.0.0.1");
        else  server_addr.sin_addr.s_addr = inet_addr(ip_sv);
	
	memset(server_addr.sin_zero, '\0', sizeof(server_addr.sin_zero));	
	
	
	//create 1 socket
	if ((sockfd = socket(AF_INET, SOCK_DGRAM, IPPROTO_UDP)) == -1) {
	        perror("client: socket");
		}

	/* localtime example */
        time_t rawtime;
	struct tm * timeinfo;
        time ( &rawtime );
        timeinfo = localtime ( &rawtime );
        printf ( "\nCurrent local time and date: %s \n", asctime (timeinfo) );  
	/*_______________________*/

	printf("PING %s (%s)\n",ip_sv,ip_sv);
        result1 = g_strdup_printf("PING %s (%s)\n",ip_sv,ip_sv);
	message(result1);message("afa");
	for(i=1;i<=n;i++){
	    Udp.stt = i;    
	    gettimeofday(&Udp.time_stamp, NULL); 
	    int trtime = Udp.time_stamp.tv_sec*1000 + (Udp.time_stamp.tv_usec/1000);
	    if ((sbytes = sendto(sockfd,(char*)&Udp, sizeof(Udp), 0, (struct sockaddr*)&server_addr, sizeof(server_addr))) == -1) {
		    perror("sendto");
		    exit(1);
	    }	   	    
            addrlen == sizeof(my_addr);	    	
            if ((rbytes = recvfrom(sockfd, buf, sizeof buf,0,(struct sockaddr*)&my_addr, &addrlen)) <= 0) {
	      perror("recvfrom");
	      close(sockfd);
	      }
            memcpy(&Udp, buf, rbytes);

    	    int timetrip = Udp.time_stamp.tv_sec*1000 + (Udp.time_stamp.tv_usec/1000);
            struct timeval tv;
       	    int triptime;
            gettimeofday(&tv, NULL); 
            triptime = tv.tv_sec*1000+(tv.tv_usec/1000);
            int  RTT = triptime -timetrip  ;
	    printf("%d bytes from %s: udp_seq %d RTT %d ms \n",rbytes,ip_sv,i,RTT);
            result = g_strdup_printf("\n %d bytes from %s: udp_seq %d RTT %d ms \n",rbytes,ip_sv,i,RTT);
	    message(result);
            sleep(1);


	}
  	close(sockfd);
  	//return 0 ;
}



```
server.c
```
#include "header.h"
int main(int argc, char *argv[])
{
 struct sockaddr_in server_addr;
 int nbytes,sockfd,addrlen;
 char buf[1000];
 udp Udp;
 // create 1 socket
 sockfd = socket(AF_INET, SOCK_DGRAM,IPPROTO_UDP);
 if(sockfd <0)
 {
   perror("socket");
   exit(1);
 }
 memset(&server_addr,0, sizeof server_addr);
 server_addr.sin_family = AF_INET;
 server_addr.sin_port = PORTSERVER;
 server_addr.sin_addr.s_addr = INADDR_ANY;
 addrlen = sizeof(server_addr);
 
 if (bind(sockfd,(struct sockaddr *)&server_addr, sizeof(struct sockaddr)) < 0) {
		close(sockfd);
		perror("bind");
		exit (2);
	}
 printf("server: waiting for connections...\n");
 for(;;){
  addrlen = sizeof(my_addr);
  if ((nbytes = recvfrom(sockfd, buf, sizeof buf,0,(struct sockaddr*)&my_addr, &addrlen)) < 0) 
    {
       perror("recvfrom");
       close(sockfd); 
    }
   else 
   {
      memcpy(&Udp, buf, nbytes);    
      printf("Recv: STT %d Size %d bytes\n",Udp.stt,nbytes);
       if ((sendto(sockfd, (char*)&Udp,sizeof(Udp),0,(struct sockaddr*)&my_addr,sizeof(my_addr))) == -1)
		  {
		    perror("sendto");
		    exit(1);
		  }  
   }
  
 }

  
}
```
form.glade
```
<?xml version="1.0" encoding="UTF-8"?>
<glade-interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window">
    <child>
      <object class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <object class="GtkFixed" id="fixed1">
            <property name="visible">True</property>
            <child>
              <object class="GtkLabel" id="label1">
                <property name="width_request">401</property>
                <property name="height_request">26</property>
                <property name="visible">True</property>
                <property name="xalign">0.51999998092651367</property>
                <property name="yalign">0.44999998807907104</property>
                <property name="label" translatable="yes">PING UDP
</property>
                <attributes>
                  <attribute name="weight" value="bold"/>
                  <attribute name="foreground" value="#f717112a112a"/>
                </attributes>
              </object>
              <packing>
                <property name="x">187</property>
                <property name="y">2</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label2">
                <property name="width_request">122</property>
                <property name="height_request">20</property>
                <property name="visible">True</property>
                <property name="label" translatable="yes">&#272;&#7873; Bài: 5</property>
                <attributes>
                  <attribute name="weight" value="ultraheavy"/>
                  <attribute name="underline" value="True"/>
                  <attribute name="foreground" value="#ffff00009d9d"/>
                </attributes>
              </object>
              <packing>
                <property name="x">317</property>
                <property name="y">30</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label3">
                <property name="width_request">300</property>
                <property name="height_request">80</property>
                <property name="visible">True</property>
                <property name="label" translatable="yes">Creator:
                Dang Tran Ngu</property>
                <attributes>
                  <attribute name="foreground" value="#16163737dcdc"/>
                </attributes>
              </object>
              <packing>
                <property name="x">412</property>
                <property name="y">53</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label4">
                <property name="width_request">100</property>
                <property name="height_request">19</property>
                <property name="visible">True</property>
                <property name="label" translatable="yes">IP Server:</property>
                <attributes>
                  <attribute name="weight" value="bold"/>
                  <attribute name="foreground" value="#1c1c1616c0c0"/>
                </attributes>
              </object>
              <packing>
                <property name="x">36</property>
                <property name="y">142</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="ip">
                <property name="width_request">160</property>
                <property name="height_request">30</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#9679;</property>
                <property name="text" translatable="yes">127.0.0.1</property>
              </object>
              <packing>
                <property name="x">135</property>
                <property name="y">136</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label5">
                <property name="width_request">70</property>
                <property name="height_request">20</property>
                <property name="visible">True</property>
                <property name="label" translatable="yes">Port: </property>
                <attributes>
                  <attribute name="weight" value="bold"/>
                  <attribute name="foreground" value="#08080000ffff"/>
                </attributes>
              </object>
              <packing>
                <property name="x">291</property>
                <property name="y">142</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="port">
                <property name="width_request">100</property>
                <property name="height_request">30</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#9679;</property>
                <property name="text" translatable="yes">6000</property>
              </object>
              <packing>
                <property name="x">347</property>
                <property name="y">137</property>
              </packing>
            </child>
            <child>
              <object class="GtkButton" id="ping">
                <property name="label" translatable="yes">PING</property>
                <property name="width_request">71</property>
                <property name="height_request">30</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <signal name="clicked" handler="on_ping_clicked"/>
              </object>
              <packing>
                <property name="x">602</property>
                <property name="y">137</property>
              </packing>
            </child>
            <child>
              <object class="GtkHSeparator" id="hseparator2">
                <property name="width_request">800</property>
                <property name="height_request">1</property>
                <property name="visible">True</property>
              </object>
              <packing>
                <property name="x">2</property>
                <property name="y">128</property>
              </packing>
            </child>
            <child>
              <object class="GtkHSeparator" id="hseparator1">
                <property name="width_request">800</property>
                <property name="height_request">2</property>
                <property name="visible">True</property>
              </object>
              <packing>
                <property name="y">184</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label6">
                <property name="width_request">60</property>
                <property name="height_request">30</property>
                <property name="visible">True</property>
                <property name="label" translatable="yes">Packet:</property>
                <attributes>
                  <attribute name="weight" value="bold"/>
                  <attribute name="foreground" value="#00000b0bffff"/>
                </attributes>
              </object>
              <packing>
                <property name="x">453</property>
                <property name="y">138</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="packet">
                <property name="width_request">50</property>
                <property name="height_request">30</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#9679;</property>
                <property name="text" translatable="yes">  4</property>
              </object>
              <packing>
                <property name="x">520</property>
                <property name="y">137</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkScrolledWindow" id="scrolledwindow1">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="hscrollbar_policy">automatic</property>
            <property name="vscrollbar_policy">automatic</property>
            <child>
              <object class="GtkTextView" id="txtshow">
                <property name="height_request">91</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="editable">False</property>
              </object>
            </child>
          </object>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <placeholder/>
        </child>
      </object>
    </child>
  </object>
  <object class="GtkSizeGroup" id="sizegroup1">
    <widgets>
      <widget name="window"/>
    </widgets>
  </object>
</glade-interface>
```

---

### Post by ngubk on 2011-09-27
I think this is a pretty simple task for anyone familiar with gcc. And Ping via UDP is pretty useful too. Much appreciate for any reply.

---

