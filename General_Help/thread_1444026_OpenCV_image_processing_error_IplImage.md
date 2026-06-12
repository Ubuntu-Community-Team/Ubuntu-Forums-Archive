---
title: "OpenCV image processing error IplImage"
date: 2010-03-31
forum: General Help
---

### Post by Mecasickle on 2010-03-31
Hey guys,

I'm having some problems on trying to figure out how I can fix the For instructions for the color Evaluation. Apparently my program works perfectly for jpg images that have square formats:such as 640 * 640 , 540 * 540, 900* 900, HOWEVER, I can't find out how I can modify the program for a rectangular image: 600*540, 800*450, and other values.

Please help me =D! Thanks in advance :

--- --- -- --

Code:

#include <time.h>
#include <ctype.h>

//using std namespace;

int main(int argc, char** argv)
{
printf("WTF");
IplImage *frame = cvLoadImage(argv[1] );
IplImage *result =cvCreateImage(cvGetSize(frame),frame->depth, 1 );

//IplImage *result =cvCreateImage(cvGetSize(frame),IPL_DEPTH_8U, 1 );
//IplImage *result = cvLoadImage(argv[1] );

//IplImage *result =cvCreateImage(cvGetSize(frame),8,1);

uchar *data, *datar;
//char *data, *datar;
int i,j,k; i=0;j=0;k=0;
int height,width,step,channel,stepr,channelr;
if (frame == NULL)
{
    puts("Unable to load the frame"); exit(0);//cout<<"error";
}

printf("frame loaded");
cvNamedWindow( "Frame", CV_WINDOW_AUTOSIZE);


//cvShowImage("Example1", frame);
cvNamedWindow( "Result", CV_WINDOW_AUTOSIZE);
//cvShowImage("Example2",result);
//show results in the end of data processing

//- Original Data sets
height=frame->height;
width=frame->width;
step=frame->widthStep;
channel=frame->nChannels;
data=(uchar *) frame->imageData;
//data=(char *) frame->imageData;
//- Result Data sets

datar= (uchar *) result->imageData;
//datar= (char *) result->imageData;
channelr=result->nChannels;
stepr=result->widthStep;

//OBS : possible values for nchannels : 1,2,3,4

for (i=0;i<(width);i++)
    {for (j=0;j<(height);j++)
        {
            if(((data[i*step+j*channel+2])>(29+data[i*step+j*channel]+29)) && ((data[i*step+j*channel+2])>(29+data[i*step+j*channel+1])))
                datar[i*stepr+j*channelr]=255;
            else
                datar[i*stepr+j*channelr]=0;
        }
    }




cvShowImage("Frame",frame);
cvShowImage("Result",result);
cvSaveImage("result.jpg",result);
cvWaitKey(0);
cvReleaseImage(&frame);
cvReleaseImage(&result);
cvDestroyWindow("Frame");
cvDestroyWindow("Result");
}

---

