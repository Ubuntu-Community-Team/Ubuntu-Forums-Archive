---
title: "gtk: ScrolledWindow, I can't figure out how to autoscroll."
date: 2010-09-23
forum: General Help
---

### Post by tjw09003 on 2010-09-23
I'm not sure how to autoscroll when text is typed in. Any help would be appreciated

```

//Autocroll Test
//Compile: gcc scrollTest.c -o scrollTest $(pkg-config --cflags --libs gtk+-2.0 gthread-2.0)


#include <stdio.h>
#include <gtk/gtk.h>

int main(int argc, char *argv[])
{

        
    GtkTextBuffer     *buffer;
        GtkWidget     *window;
        GtkWidget     *fixed;
        GtkWidget     *label;
        GtkWidget     *textview;
        GtkWidget    *scrollCont;
        

        gtk_init(&argc, &argv);
        window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

        gtk_window_set_title(GTK_WINDOW(window), "scrollTest");
        gtk_window_set_default_size(GTK_WINDOW(window), 350, 250);
        g_signal_connect( G_OBJECT( window ), "destroy", G_CALLBACK( gtk_main_quit ), NULL );
        

    fixed = gtk_fixed_new();
    textview = gtk_text_view_new();

    
    scrollCont = gtk_scrolled_window_new(NULL, NULL);
    gtk_scrolled_window_set_policy (GTK_SCROLLED_WINDOW (scrollCont), GTK_POLICY_AUTOMATIC, GTK_POLICY_AUTOMATIC);
    gtk_scrolled_window_add_with_viewport(GTK_SCROLLED_WINDOW(scrollCont), textview);
    gtk_widget_set_size_request(scrollCont, 300, 200);
    
    buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW(textview));
    gtk_text_buffer_set_text(buffer, "scrollTEST :'(", -1);
    
        gtk_container_add(GTK_CONTAINER(window),fixed);
    gtk_fixed_put(GTK_FIXED(fixed), scrollCont, 5, 5);



        gtk_widget_show_all(window);
    
        gtk_main();
    return 0;
}


```

---

