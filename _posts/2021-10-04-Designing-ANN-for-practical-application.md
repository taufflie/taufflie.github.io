Lab report AI: Designing ANN for practical application              Vincent TAUFFLIEB
Hardware used: I7 core, 8GB RAM
Application 1: AND GATE
We designed an ANN with forward and back propagation to predict the AND GATE truth table. Below is the code to set up the correct weights and to compare the predicted label and the Ground Truth.
 
 ![image](https://user-images.githubusercontent.com/91050310/137277340-f32791c5-216c-4596-aacc-c042487f7c23.png)
![image](https://user-images.githubusercontent.com/91050310/137277356-5e8c3502-dd45-42ba-a119-4b19951510f3.png)


The forward propagation function, which return the predicted label for an input given the weight matrix and the bias, is defined as follow :

 ![image](https://user-images.githubusercontent.com/91050310/137277367-60db1659-863c-4f11-b9c2-2c7393339345.png)


Exercise 1 : Number of epochs to obtain valid predictions
To calculate this number we change the first for loop into a while loop that compares the predicted label and the Ground Truth. We add a counter to track the number of epochs. In the end, we need 24 eopchs to have valid predictions.
 ![image](https://user-images.githubusercontent.com/91050310/137277379-cf828c8c-dae0-4876-bfeb-cbde13b2c2a0.png)


Exercise 2: Prediction for OR GATE
To perform the prediction for the OR GATE, we just change the label vector as follow. We need 16 epochs to have the right predictions.
 ![image](https://user-images.githubusercontent.com/91050310/137277382-64525a7e-033d-4f4e-b700-243f22b815bf.png)


 
Exercise 3: Sigmoid activation function
We define the sigmoid function as follow:
 ![image](https://user-images.githubusercontent.com/91050310/137277393-f43c8bfa-40f5-4e3f-a023-e6f7f3b8f6bb.png)

In the forward propagation function, we change the activation function for this one. The sigmoid function only returns value between 0 and 1 so it will never have the exact result. 
 ![image](https://user-images.githubusercontent.com/91050310/137277405-f9479ed5-4503-4228-84bb-a70c1934aeba.png)


The step unit function can return 0 and 1 which ensure that we will have convergence.
 ![image](https://user-images.githubusercontent.com/91050310/137277420-79fbd87a-f792-4d46-ac67-ebeeb7037f02.png)


Application 2: XOR GATE
For this application, we designed a simple 2-layer ANN, using 2 neurons in the first layer and 1 in the second. As in the previous application, we initialize the weights randomly and then perform both the back and forward propagation. We use here a sigmoid activation function.
 ![image](https://user-images.githubusercontent.com/91050310/137277427-3714372f-1092-4106-88f9-43be1fbc127a.png)
![image](https://user-images.githubusercontent.com/91050310/137277434-cb354539-4787-4611-89ae-7247eb500f9b.png)

 
Exercise 4: Minimum number of epochs to have an error below 0.01
As before, we change the for loop into a while loop to have this number. We use a condition over the error of prediction and we implement a counter. 
 ![image](https://user-images.githubusercontent.com/91050310/137277443-bacfa87f-d1c5-4bdb-b16a-179584288bca.png)

In the end, we need between 1400 and 3000 epochs to have an error inferior to 0.01. This number fluctuates because we randomly set the initial weights and bias. Sometimes, the algortihm does not converge at all.
 
 ![image](https://user-images.githubusercontent.com/91050310/137277453-f0cb5271-4921-41d8-bce7-f755550a9af3.png)
![image](https://user-images.githubusercontent.com/91050310/137277465-9f15f1fd-0f34-4c7d-83c3-94a27a258104.png)
![image](https://user-images.githubusercontent.com/91050310/137277469-b167aac6-129e-45fd-a576-43933c8ba230.png)

 
Exercise 5: Hyperbolic tangent as activation function
We define the hyperbolic tangent function and its derivate. We change the activation function in the main.
 ![image](https://user-images.githubusercontent.com/91050310/137277475-1cf868f8-25ad-4e5d-a335-a22dd52a0488.png)

Here are different results that we can get:
 
 ![image](https://user-images.githubusercontent.com/91050310/137277484-3345d7f2-8f06-4380-979d-b8517ad55aa4.png)
![image](https://user-images.githubusercontent.com/91050310/137277488-14068802-26c8-4bdf-a20c-577de6edc6e9.png)
![image](https://user-images.githubusercontent.com/91050310/137277497-50c2a10e-ea98-47dc-97a3-019e1c83cf49.png)


 
We can observe that the number of epochs has greatly decreased and is between 150 and 200. The predicted value also seems closer to the GT when it is close to 0 and seem a bit less accurate when it is close to 1.
 ![image](https://user-images.githubusercontent.com/91050310/137277510-9b062ff8-721b-4e03-8e05-d2c54feb66d5.png)

This may be explained by the fact tanh functions has output values between [-1,1] which means the function is symmetric and that the inputs will produce outputs centred around its mean = 0.
Exercise 6 : Number of trainable parameters
The number of trainable parameters can be calculated as follow :
4 parameters for W1, 2 parameters for W2, 2 parameter for B1 and 1 parameter for B2. So in total, we have 9 parameters to train.
The ANN performances are influenced by the initialization of the variables as mentionned in Exercice 4 and 5.
Exercise 7 : ANN architecture with Tensorflow
We write the python script for the AND GATE with tensorflow as follow. We use only one layer with 1 neuron for this one as in the previous application.
 
 ![image](https://user-images.githubusercontent.com/91050310/137277520-355d8d7b-89e1-4e64-8272-7c3a2677874a.png)
![image](https://user-images.githubusercontent.com/91050310/137277534-73dc27de-514a-4df7-be81-59bb4fa395cb.png)

We use 3000 epochs considering the previous results of Exercice 4. We obtained the following results : 
 ![image](https://user-images.githubusercontent.com/91050310/137277545-c5a0cc29-0735-4621-836c-2e2d44efe590.png)

For the XOR GATE, we change the labels and add a layer as follow : 
 ![image](https://user-images.githubusercontent.com/91050310/137277550-f50f1ec7-080e-4c73-9cba-6ad4b487d50e.png)
![image](https://user-images.githubusercontent.com/91050310/137277555-2769cff9-24cc-41f0-abf1-7cac5072fc29.png)

 
We have the following results :
 ![image](https://user-images.githubusercontent.com/91050310/137277562-7ffec93d-7f2b-401a-b9db-6c08d0e9be20.png)

For the 2 scripts, the results seem to close to the right label. We would need more epochs to have a better result.







Application 3: Regression House Price Market
We use an ANN designed with Tensorfflow in this application to make a regression on the house price market given some inputs. We used a 2-layer ANN.
  
![image](https://user-images.githubusercontent.com/91050310/137277569-be6730d6-2163-462a-bd61-dd7e2ef50772.png)
![image](https://user-images.githubusercontent.com/91050310/137277575-dfb27135-9628-461c-a769-0188e084f4e2.png)

 
Here are some of the predicted prices and the corresponding true prices. 
![image](https://user-images.githubusercontent.com/91050310/137277584-f928c0bd-8c48-40ce-b3a5-c42e7be17c34.png)

 
Exercise 8 : Mean square error
We set up the MSE and run the algortihm a few times : 

 ![image](https://user-images.githubusercontent.com/91050310/137277592-94afa1d6-40cf-4bd4-bee6-b50d329a8fa9.png)
![image](https://user-images.githubusercontent.com/91050310/137277607-12e88f76-3b80-41ef-b325-134575b7ccc0.png)
![image](https://user-images.githubusercontent.com/91050310/137277615-b872ba81-d6b1-435f-a6c9-e424323a5f71.png)
![image](https://user-images.githubusercontent.com/91050310/137277623-0434450c-3f2a-4b99-ad33-de3956b0bade.png)
 ![image](https://user-images.githubusercontent.com/91050310/137277631-28e72307-2207-4bf7-a427-ad1be52e313a.png)

 
  
 


On average, we have an error of 0.116 thousand of dollars. 

Exercise 9: Different values of MSE
Before training the ANN, we shuffle the data which changes the training set each time. Some of them may output a better training model than others.

Exercise 10: MSE with 1 additional layer
We add a layer in the model as follow :


![image](https://user-images.githubusercontent.com/91050310/137277642-f09fab10-e568-4f30-ad1d-d79889118be0.png)
![image](https://user-images.githubusercontent.com/91050310/137277646-e5bfe10f-90e3-4a7c-a2ca-2fa60b7630aa.png)
![image](https://user-images.githubusercontent.com/91050310/137277654-16359f13-ff19-40f4-813f-2f56f1c41949.png)
![image](https://user-images.githubusercontent.com/91050310/137277662-1481de4d-c308-469f-826b-3e0a95d952c1.png)


 
 
  
The MSE seem to be a bit better. On average, we have an error of 0.090 thousand of dollars. Having a an additional layer seem to improve a bit the predictions but it is more costly.

Exercise 11: Prediction of Nitric oxides concentration
To predict this, we just change the input and output labels as follow. The old ones are:
 ![image](https://user-images.githubusercontent.com/91050310/137277687-b9c05d7f-294e-4b7c-82d6-c9aa6aaa421d.png)

And the new ones are :
 
![image](https://user-images.githubusercontent.com/91050310/137277694-8b72e737-603c-4cf9-ba7c-85b08edde349.png)
![image](https://user-images.githubusercontent.com/91050310/137277704-a0784387-f0a0-490d-a7fd-204702e63e1e.png)
![image](https://user-images.githubusercontent.com/91050310/137277717-a982b7f8-9a40-4f1d-938b-80d85bdc73bb.png)
![image](https://user-images.githubusercontent.com/91050310/137277724-0b188759-8d74-4280-aefc-6d43bdab727f.png)

 
 
 
The average MSE is 4.8e-05 parts per 10 million.
