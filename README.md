# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char text[100];
    int key[3][3], i, j, k, len;
    int block[3], result[3];

    printf("Enter plaintext: ");
    scanf("%s", text);

    printf("Enter 3x3 key matrix (9 integers):\n");
    for (i = 0; i < 3; i++) {
        for (j = 0; j < 3; j++) {
            scanf("%d", &key[i][j]);
        }
    }

    len = strlen(text);

    for (i = 0; i < len; i++) {
        text[i] = toupper(text[i]);
    }

    while (len % 3 != 0) {
        text[len++] = 'X';
    }
    text[len] = '\0';

    printf("Cipher text: ");

    for (i = 0; i < len; i += 3) {
        for (j = 0; j < 3; j++) {
            block[j] = text[i + j] - 'A';
        }

        for (j = 0; j < 3; j++) {
            result[j] = 0;
            for (k = 0; k < 3; k++) {
                result[j] += key[j][k] * block[k];
            }
            result[j] %= 26;
        }

        for (j = 0; j < 3; j++) {
            printf("%c", result[j] + 'A');
        }
    }

    printf("\n");

    return 0;
}
```
## OUTPUT
<img width="1622" height="917" alt="Screenshot 2026-10-26 112633" src="https://github.com/user-attachments/assets/84440f79-90e6-49aa-b5f7-672447760fe9" />

## RESULT
Thus the implementation of hill cipher had been executed successfully.
