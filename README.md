# priorty_queue
 /* Program for implementing priority queues */
#include<stdio.h>
#include<stdlib.h>
#define MAX 3
struct myqueue {
 int f, r;
 int a[MAX];
};
typedef struct myqueue pqueue;
void insert(pqueue *);
void delete(pqueue *);
void display(pqueue *, pqueue *, pqueue *);
int isempty(pqueue *);
int isfull(pqueue *);
 
int main() {
 pqueue q[3];
 int ch, i, n;
 for (i = 0; i < 3; i++) {
  q[i].f = 0;
  q[i].r = -1;
 }
 while (1) {
  printf("\n******* MENU ********\n");
  printf("1.Insert\n2.Delete\n3.Display\n4.Exit");
  printf("\nEnter your choice:\n");
  scanf("%d", &ch);
  switch (ch) {
  case 1:
   printf("\nEnter priority:\n");
   scanf("%d", &n);
   insert(&q[n - 1]);
   break;
 
  case 2:
   if (isempty(&q[0])) {
    if (isempty(&q[1])) {
     if (isempty(&q[2])) {
      printf("\nAll queues are empty..\n");
      break;
     } else
      n = 2;
    } else
     n = 1;
   } else
    n = 0;
   delete(&q[n]);
   break;
 
  case 3:
   display(&q[0], &q[1], &q[2]);
   break;
  case 4:
   exit(0);
  default:
   printf("\nInvalid choice..");
   break;
  }
 }
}
 
int isempty(pqueue *q) {
 if (q->f > q->r)
  return 1;
 else
  return 0;
}
 
int isfull(pqueue *q) {
 if (q->r == MAX - 1)
  return 1;
 else
  return 0;
}
 
void insert(pqueue *q) {
 int x;
 if (isfull(q)) {
  printf("\nQueue overflow..");
  return;
 } else {
  printf("\nEnter the element to be inserted:\n");
  scanf("%d", &x);
  (q->r)++;
  q->a[q->r] = x;
 }
}
 
void delete(pqueue *q) {
 int n;
 n = q->a[q->f];
 (q->f)++;
 printf("The deleted element is = %d", n);
}
 
void display(pqueue *q1, pqueue *q2, pqueue *q3) {
 int i;
 if (isempty(q1))
  printf("\nQueue1 is empty..");
 else
  printf("\nThe contents of queue1 are:\n");
 for (i = q1->f; i <= (q1->r); i++) {
  printf("%d\t", q1->a[i]);
 }
 if (isempty(q2))
  printf("\nQueue2 is empty..");
 else
  printf("\nThe contents of queue2 are:\n");
 for (i = q2->f; i <= (q2->r); i++) {
  printf("%d\t", q2->a[i]);
 }
 if (isempty(q3))
  printf("\nQueue3 is empty..");
 else
  printf("\nThe contents of queue3 are:\n");
 for (i = q3->f; i <= (q3->r); i++) {
  printf("%d\t", q3->a[i]);
 }
}
 
