 Overview
This project demonstrates the implementation of a **Queue data structure using a Linked List** in C.

A Queue follows the **FIFO (First In, First Out)** principle:
- The first element inserted is the first element removed.

Unlike array implementation, a linked list queue:
- Does not have a fixed size.
- Grows dynamically using memory allocation.
- Uses `front` and `rear` pointers for efficient operations.

---

 Source Code

```c
#include <stdio.h>
#include <stdlib.h>

// Define structure for node
struct Node {
    int data;
    struct Node* next;
};

// Declare front and rear pointers
struct Node* front = NULL;
struct Node* rear = NULL;

// Check if queue is empty
int isEmpty() {
    return (front == NULL);
}

// Enqueue operation
void enqueue(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

    if (newNode == NULL) {
        printf("Heap Overflow!\n");
        return;
    }

    newNode->data = value;
    newNode->next = NULL;

    if (isEmpty()) {
        front = rear = newNode;
    } else {
        rear->next = newNode;
        rear = newNode;
    }

    printf("Inserted: %d\n", value);
}

// Dequeue operation
void dequeue() {
    if (isEmpty()) {
        printf("Queue is Empty!\n");
        return;
    }

    struct Node* temp = front;
    printf("Deleted: %d\n", front->data);

    front = front->next;

    if (front == NULL) {
        rear = NULL;
    }

    free(temp);
}

// Display queue
void display() {
    if (isEmpty()) {
        printf("Queue is Empty!\n");
        return;
    }

    struct Node* temp = front;
    printf("Queue elements: ");

    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }

    printf("\n");
}

// Main function
int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);

    display();

    dequeue();
    dequeue();

    display();

    return 0;
}
```

---

 Explanation

 Structure
- `struct Node` contains:
  - `data` → Stores queue element.
  - `next` → Points to next node.

 Pointers Used
- `front` → Points to the first element.
- `rear` → Points to the last element.

 Enqueue Operation
- Allocates memory for new node.
- If queue is empty → `front = rear = newNode`.
- Otherwise → `rear->next = newNode` and update `rear`.

 Dequeue Operation
- Removes node from `front`.
- Updates `front` pointer.
- If queue becomes empty → set `rear = NULL`.
-  Display Operation
- Traverses from `front` to `NULL`.

---

 Sample Output

```
Inserted: 10
Inserted: 20
Inserted: 30
Queue elements: 10 20 30
Deleted: 10
Deleted: 20
Queue elements: 30
```

---

 Time Complexity

- Enqueue: **O(1)**
- Dequeue: **O(1)**
- Display: **O(n)**

---

 Advantages Over Array Queue

- No fixed size limitation
- Dynamic memory usage
- Efficient insertion and deletion

---

 How to Compile and Run

 Compile:
```
gcc queue_linkedlist.c -o queue
```
 Run:
```
./queue
```

---

Concepts Used
- Structures in C
- Pointers
- Dynamic Memory Allocation (`malloc`, `free`)
- Queue Data Structure
- FIFO Principle

---



---

⭐ If you found this helpful, cons
