import streamlit as st


def calculo():
    st.title("Calculadora Simples")

    num1 = st.number_input("Digite o primeiro número:")
    num2 = st.number_input("Digite o segundo número:")

    operacao = st.selectbox("Selecione a operação:", ["Soma", "Subtração", "Multiplicação", "Divisão", "Potenciação"])
    if st.button('Calcular'):
        if operacao == "Soma":
            resultado = num1 + num2
        elif operacao == "Subtração":
            resultado = num1 - num2
        elif operacao == "Multiplicação":
            resultado = num1 * num2
        elif operacao == "Potenciação":
            resultado = num1 ** num2
        else:
            resultado = num1 / num2

        st.write("Resultado:", resultado)


def conversor():
    st.title("Conversor de temperatura")

    temperatura = st.number_input("Digite o primeiro número:")
    medida = st.selectbox("Selecione a medida:", ['Celsius (C)', 'Kelvin (K)', 'Fahrenheit (F)'])
    st.write('|')
    medida2 = st.selectbox('Para qual medida deseja converter:', ['Celsius (C)', 'Kelvin (K)', 'Fahrenheit (F)'])

    if st.button('Converter'):
        if medida == 'Celsius (C)' and medida2 == 'Fahrenheit (F)':
            converção = (temperatura * 1.8) + 32
        elif medida == 'Celsius (C)' and medida2 == 'Kelvin (K)':
            converção = temperatura + 273
        elif medida == 'Fahrenheit (F)' and medida2 == 'Celsius (C)':
            converção = (temperatura - 32) / 1.8
        elif medida == 'Fahrenheit (F)' and medida2 == 'Kelvin (K)':
            converção = (temperatura + 459) * 5 / 9
        elif medida == 'Kelvin (K)' and medida2 == 'Celsius (C)':
            converção = temperatura - 273
        elif medida == 'Kelvin (K)' and medida2 == 'Fahrenheit (F)':
            converção = (temperatura - 273) * 9 / 5 + 32

        st.write('Resultado: ', converção)


with st.sidebar:
    st.title('')
    Escolha = st.selectbox('Escolha um modo:', ['Calculadora Simples', 'Conversor de temperatura'])

if Escolha == 'Calculadora Simples':
    calculo()

else:
    conversor()

