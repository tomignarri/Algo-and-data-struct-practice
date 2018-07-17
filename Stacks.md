# Algo-and-data-struct-practice
My answers to textbook exercises (Building Java Programs and CTCI)



package stackpractice;

import java.util.*;


public class StackPractice {

    
    public static void main(String[] args) {
        String[] data = {"to", "be", "or", "not", "to", "be"};
        int[] dataInt = {2, 6, 8, 1, 3, 9, 4, 7};
        
        Stack<String> s = new Stack<String>();
        Stack<Integer> sInt = new Stack<Integer>(); 
        
        for(int i : dataInt){
            sInt.add(i);
        }
        
        //System.out.println(sum(sInt));
        //System.out.println(sInt);
        
        //splitStack(sInt);
        stutter(sInt);
        
        

    }
    
    public static int sum(Stack<Integer> s){
        int sum = 0;
        Queue<Integer> q = new LinkedList<Integer>();
        while (!s.isEmpty()) {
            int n = s.pop();
            sum += n;
            q.add(n);
        }
        queueToStack(q, s);
        stackToQueue(s, q);
        queueToStack(q, s);
        return sum;
    }
    
    public static void queueToStack(Queue<Integer> q, Stack<Integer> s) {
        while (!q.isEmpty()) {
            int n = q.remove();
            s.push(n);
        }
    }
    
    public static void stackToQueue(Stack<Integer> s, Queue<Integer> q) {
        while (!s.isEmpty()) {
            int n = s.pop();
            q.add(n);
        }
    }

    // add everything to q...if less than target, add to stack 
    // else add back to end of q
    public static void splitStack(Stack<Integer> s){
        Queue<Integer> q = new LinkedList<Integer>();
        int count = 0;
        while(!s.isEmpty()){
            int n = s.pop();
            q.add(n);
        }
        while(count != q.size()){
            int n = q.remove();
            if(n <= 5){
                s.add(n);
            } else {
                q.add(n);
                count++;// count and size are the same when there are no more 
                        // num less than 5...this sets limit on how far loop 
                        // can iterate thru q
            }
        }
        while(!q.isEmpty()){
            int n = q.remove();
            s.add(n);
        }
        System.out.println(s);
        
    }
    
    public static void stutter(Stack<Integer> s){
        Queue<Integer> q = new LinkedList<Integer>();
        while(!s.isEmpty()){
            int n = s.pop();
            q.add(n);
        }
        while(!q.isEmpty()){//double each number
            int n = q.remove();
            s.push(n);
            s.push(n);
        }
        while(!s.isEmpty()){// s to q
            int n = s.pop();
            q.add(n);
        }
        while(!q.isEmpty()){// q to s
            int n = q.remove();
            s.push(n);
        }
        System.out.println(s);
    }
    
    
    
}
