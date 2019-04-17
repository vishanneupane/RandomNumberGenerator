# RandomNumberGenerator
//Used executed function and created two threads
//Vishan Neupane

import java.util.concurrent.*;


public class RandomNumberGenerator
{
    public static void main(String[] args)
    {
        ExecutorService service = Executors.newFixedThreadPool(2);

        service.execute(new Oddnumbers());
        service.execute(new PrintConsonant());
	service.shutdown();
    }
}



class Oddnumbers implements Runnable
{
    public void run()
    {
        for(int i=1; i<29; i++)
        {
            if(i%2 != 0)
            {
                System.out.println(i + " ");
            }
        }
    }
}



class PrintConsonant implements Runnable
{
    public void run()
    {
        String line = "abcdefghijklmnopqrstuvwxyz";

        for(int i = 0; i < line.length(); ++i)
        {
            char ch = line.charAt(i);

            if(ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u')
            {
                continue;
            }

            else if((ch >= 'a'&& ch <= 'z'))
            {
                System.out.println(ch + "");
            }

        }
    }
}
