<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>X1SCRIPT - Gerador de Script WhatsApp</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #111827; /* Grafite escuro (Cool Gray 900) */
            color: #F3F4F6; /* Cinza claro para texto principal (Cool Gray 100) */
        }
        .font-title {
            font-family: 'Inter', sans-serif;
            font-weight: 800;
        }
        .modern-header {
            background-color: #1F2937; /* Grafite um pouco mais claro (Cool Gray 800) */
            border-bottom: 1px solid #374151; /* Cool Gray 700 para borda sutil */
        }
        .modern-header h1 {
            color: #FFFFFF;
        }
        .modern-header p {
             color: #9CA3AF; /* Cool Gray 400 */
        }

        .main-content-card {
            background-color: #1F2937;
            border-radius: 12px;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        .form-label {
            color: #D1D5DB; /* Cool Gray 300 */
            font-weight: 500;
        }
        .form-input, .form-textarea {
            background-color: #374151; /* Cool Gray 700 */
            color: #F3F4F6;
            border: 1px solid #4B5563; /* Cool Gray 600 */
            border-radius: 8px;
            padding: 12px 16px;
        }
        .form-input::placeholder, .form-textarea::placeholder {
            color: #9CA3AF;
        }
        .form-input:focus, .form-textarea:focus {
            outline: none;
            border-color: #10B981; /* Verde Esmeralda 500 */
            box-shadow: 0 0 0 3px rgba(16, 185, 129, 0.3);
        }
        .modern-button-primary {
            background-image: linear-gradient(to right, #10B981, #059669);
            color: #FFFFFF;
            font-weight: 600;
            border-radius: 8px;
            padding: 12px 16px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        .modern-button-primary:hover {
            background-image: linear-gradient(to right, #059669, #047857);
            box-shadow: 0 7px 14px rgba(0,0,0,0.1), 0 3px 6px rgba(0,0,0,0.08);
            transform: translateY(-1px);
        }
        .modern-button-primary:disabled {
            background-image: none;
            background-color: #4B5563;
            color: #9CA3AF;
            cursor: not-allowed;
            box-shadow: none;
            transform: none;
        }

        .chat-results-area { /* Mantém o card externo como está */
            background-color: #1F2937;
            border-radius: 12px;
        }
        .chat-results-title {
            color: #FFFFFF;
            font-weight: 700;
        }
        /* Ajustes para o visual WhatsApp Dark Mode Preview */
        .messages-container-modern {
            background-color: #0b141a; /* Fundo de chat escuro do WhatsApp */
            border-radius: 8px;
            padding: 16px;
        }
        .message-bubble-modern { /* Estilo base para todos os balões na área de preview */
            max-width: 85%;
            word-wrap: break-word;
            border-radius: 7.5px; /* Raio de borda típico do WhatsApp */
            padding: 8px 12px; /* Padding típico */
            color: #e9edef; /* Cor de texto clara padrão para modo escuro */
        }
        .message-sent-modern {
            background-color: #005C4B; /* Verde escuro do balão enviado no WhatsApp Dark */
            align-self: flex-end;
            /* Mantém o formato da "cauda" do balão */
            border-radius: 7.5px 7.5px 0px 7.5px;
        }
        .message-header-modern {
            /* O WhatsApp não costuma ter um header explícito "Mensagem X" dentro do balão.
               Mas se mantivermos, a cor precisa contrastar bem com #005C4B.
               Um verde muito claro ou um cinza claro.
            */
            color: #A7F3D0; /* Verde Esmeralda 200 - pode precisar de ajuste fino */
            font-weight: 500; /* Mais suave */
            font-size: 0.75rem; /* Menor */
            margin-bottom: 2px; /* Menos espaço */
        }
        .placeholder-highlight-modern {
            color: #53BDEB; /* Azul claro para placeholders, comum em temas escuros */
            background-color: rgba(83, 189, 235, 0.15);
            font-weight: 600;
            padding: 1px 3px;
            border-radius: 4px;
        }
        .variation-button-modern {
            background-color: #202C33; /* Cinza escuro para botões secundários no WhatsApp Dark */
            color: #8696A0; /* Cinza claro para texto do botão */
            border: 1px solid #374045; /* Borda sutil */
            font-size: 0.75rem;
            padding: 4px 8px;
            border-radius: 15px; /* Botões mais arredondados */
        }
        .variation-button-modern:hover {
            background-color: #2a3942;
            color: #a2b0b9;
        }
        .variation-bubble-modern {
            background-color: #202C33; /* Cinza escuro para variações, como outros elementos de UI no WhatsApp Dark */
            border: 1px solid #374045; /* Borda sutil */
            color: #e9edef; /* Texto claro */
            font-size: 0.85rem;
            border-radius: 7.5px;
        }
        /* Fim dos ajustes para WhatsApp Dark Mode Preview */

        .modern-button-secondary {
            background-color: transparent;
            color: #10B981;
            border: 1px solid #10B981;
            font-weight: 600;
        }
        .modern-button-secondary:hover {
            background-color: rgba(16, 185, 129, 0.1);
            color: #34D399;
        }
        .tone-analysis-modern {
            background-color: #1F2937;
            border: 1px solid #374151;
            border-radius: 8px;
        }
        .tone-analysis-modern h3 {
            color: #10B981;
            font-weight: 700;
        }
        .tone-analysis-modern p {
            color: #D1D5DB;
        }
        .loader {
            border: 5px solid #374151;
            border-top: 5px solid #10B981;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }
        .small-loader {
            border: 3px solid #374151;
            border-top: 3px solid #10B981;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            animation: spin 1s linear infinite;
            display: inline-block;
            margin-left: 8px;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        #mensagens-container::-webkit-scrollbar,
        .variations-container::-webkit-scrollbar {
            width: 6px; /* Scrollbar mais fina */
        }
        #mensagens-container::-webkit-scrollbar-track,
        .variations-container::-webkit-scrollbar-track  {
            background: #0b141a; /* Fundo da trilha igual ao chat */
            border-radius: 10px;
        }
        #mensagens-container::-webkit-scrollbar-thumb,
        .variations-container::-webkit-scrollbar-thumb {
            background: #374045; /* Cor do thumb da scrollbar no WhatsApp Dark */
            border-radius: 10px;
        }
        #mensagens-container::-webkit-scrollbar-thumb:hover,
        .variations-container::-webkit-scrollbar-thumb:hover {
            background: #4a545c;
        }
        .error-message-modern {
            background-color: #FEF2F2;
            border: 1px solid #F87171;
            color: #DC2626;
            border-radius: 8px;
        }
        .error-message-modern strong {
            color: #B91C1C;
        }
    </style>
</head>
<body class="flex flex-col min-h-screen">

    <header class="modern-header p-5 shadow-lg">
        <div class="container mx-auto max-w-3xl text-center">
            <h1 class="text-4xl md:text-5xl font-title">X1SCRIPT</h1>
            <p class="text-md opacity-80 mt-1">Seu gerador de scripts de venda para WhatsApp com IA</p>
        </div>
    </header>

    <main class="flex-grow container mx-auto max-w-3xl p-4 md:p-6">
        <div class="main-content-card p-6 md:p-8">
            <form id="geradorForm" class="space-y-6">
                <div>
                    <label for="nicho" class="block text-sm form-label mb-2">Qual o seu Nicho de Mercado?</label>
                    <input type="text" id="nicho" name="nicho" placeholder="Ex: Saúde e Bem-estar, Educação Online, SaaS" required
                           class="w-full form-input transition duration-150 ease-in-out">
                </div>

                <div>
                    <label for="objetivo" class="block text-sm form-label mb-2">Qual o seu Objetivo de Venda?</label>
                    <textarea id="objetivo" name="objetivo" rows="4" placeholder="Ex: Vender meu curso de yoga, Agendar demonstração do software, Apresentar plano de assinatura" required
                              class="w-full form-textarea transition duration-150 ease-in-out"></textarea>
                </div>

                <button type="submit" id="submitButton"
                        class="w-full modern-button-primary py-3.5 px-4 flex items-center justify-center text-lg">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6 mr-2.5">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9.813 15.904L9 18.75l-.813-2.846a4.5 4.5 0 00-3.09-3.09L2.25 12l2.846-.813a4.5 4.5 0 003.09-3.09L9 5.25l.813 2.846a4.5 4.5 0 003.09 3.09L15.75 12l-2.846.813a4.5 4.5 0 00-3.09 3.09zM18.259 8.715L18 9.75l-.259-1.035a3.375 3.375 0 00-2.455-2.456L14.25 6l1.036-.259a3.375 3.375 0 002.455-2.456L18 2.25l.259 1.035a3.375 3.375 0 002.456 2.456L21.75 6l-1.035.259a3.375 3.375 0 00-2.456 2.456zM16.894 20.567L16.5 21.75l-.394-1.183a2.25 2.25 0 00-1.423-1.423L13.5 18.75l1.183-.394a2.25 2.25 0 001.423-1.423l.394-1.183.394 1.183a2.25 2.25 0 001.423 1.423l1.183.394-1.183.394a2.25 2.25 0 00-1.423 1.423z" />
                    </svg>
                    Gerar Script com IA
                </button>
            </form>
        </div>

        <div id="script-resultado" class="mt-10 md:mt-12 chat-results-area p-5 md:p-6" style="display: none;">
            <h2 class="text-2xl md:text-3xl font-title chat-results-title mb-6 text-center">Seu Script de 10 Mensagens:</h2>
            <div id="loadingIndicator" class="loader" style="display: none;"></div>
            <div id="error-message" class="error-message-modern px-4 py-3 relative mb-4" role="alert" style="display: none;">
                <strong class="font-bold">Ops!</strong>
                <span class="block sm:inline">Algo deu errado. Por favor, tente novamente.</span>
            </div>
            <div id="mensagens-container" class="messages-container-modern space-y-3 overflow-y-auto max-h-[60vh] md:max-h-[65vh]">
                </div>
            <p class="text-xs text-gray-500 mt-6 text-center">
                Lembre-se: este script é uma sugestão. Adapte os marcadores <code class="placeholder-highlight-modern px-1 rounded">[ENTRE COLCHETES]</code> e o tom à sua marca.
            </p>
            <div class="mt-8 space-y-3">
                <button id="copyAllButton" class="w-full modern-button-secondary py-2.5 px-4 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:ring-opacity-50 transition duration-150 ease-in-out flex items-center justify-center" style="display: none;">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 17.25v3.375c0 .621-.504 1.125-1.125 1.125h-9.75a1.125 1.125 0 01-1.125-1.125V7.875c0-.621.504-1.125 1.125-1.125H6.75a9.06 9.06 0 011.5.124m7.5 10.376h3.375c.621 0 1.125-.504 1.125-1.125V11.25c0-4.46-3.243-8.161-7.5-8.876a9.06 9.06 0 00-1.5-.124H9.375c-.621 0-1.125.504-1.125 1.125v3.5m7.5 10.375H9.375a1.125 1.125 0 01-1.125-1.125v-9.25m12 6.625v-1.875a3.375 3.375 0 00-3.375-3.375h-1.5a1.125 1.125 0 01-1.125-1.125v-1.5a3.375 3.375 0 00-3.375-3.375H9.75" />
                    </svg>
                    Copiar Todas as Mensagens
                </button>
                <button id="analyzeToneButton" class="w-full modern-button-secondary py-2.5 px-4 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:ring-opacity-50 transition duration-150 ease-in-out flex items-center justify-center" style="display: none;">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M7.5 8.25h9m-9 3H12m-6.75 3h9m-9 3H12zm0 0h.008v.008H7.5V18zm0 0H5.625m2.625 0h2.625m0 0h2.625m2.625 0h2.625M3.75 6H20.25M3.75 12H20.25m-16.5 6H20.25" />
                    </svg>
                    Analisar Tom do Script ✨
                </button>
            </div>
            <div id="tone-analysis-result" class="mt-6 tone-analysis-modern p-4" style="display: none;">
                <h3 class="text-lg font-title mb-2">Análise de Tom do Script:</h3>
                <div id="tone-loadingIndicator" class="small-loader" style="display: none;"></div>
                <p id="tone-analysis-text" class="text-sm"></p>
            </div>
        </div>
    </main>

    <footer class="modern-header text-center p-6 mt-auto border-t-2 border-b-0">
        <p class="text-sm">&copy; <span id="currentYear"></span> X1SCRIPT - Gerando conversas que convertem.</p>
    </footer>

    <script>
        document.getElementById('currentYear').textContent = new Date().getFullYear();

        const form = document.getElementById('geradorForm');
        const nichoInput = document.getElementById('nicho');
        const objetivoInput = document.getElementById('objetivo');
        const resultadoDiv = document.getElementById('script-resultado');
        const mensagensContainer = document.getElementById('mensagens-container');
        const loadingIndicator = document.getElementById('loadingIndicator');
        const errorMessageDiv = document.getElementById('error-message');
        const submitButton = document.getElementById('submitButton');
        const copyAllButton = document.getElementById('copyAllButton');
        const analyzeToneButton = document.getElementById('analyzeToneButton');
        const toneAnalysisResultDiv = document.getElementById('tone-analysis-result');
        const toneLoadingIndicator = document.getElementById('tone-loadingIndicator');
        const toneAnalysisText = document.getElementById('tone-analysis-text');

        let currentScriptMessages = [];

        async function callGeminiAPI(prompt, isJsonOutput = true) {
            let chatHistory = [{ role: "user", parts: [{ text: prompt }] }];
            const payload = { contents: chatHistory };

            if (isJsonOutput) {
                payload.generationConfig = {
                    responseMimeType: "application/json",
                };
                if (prompt.includes("Analise o tom geral")) {
                     payload.generationConfig.responseSchema = {
                        type: "OBJECT",
                        properties: { "analise_tom": { "type": "STRING" } }
                    };
                } else { // Para scripts e variações
                     payload.generationConfig.responseSchema = {
                        type: "ARRAY", items: { "type": "STRING" }
                    };
                }
            }
            
            const apiKey = "";
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

            const response = await fetch(apiUrl, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(payload)
            });

            if (!response.ok) {
                const errorData = await response.json();
                console.error("Erro da API Gemini:", errorData);
                throw new Error(`Erro de API: ${response.statusText} - ${errorData?.error?.message || 'Detalhes não disponíveis'}`);
            }
            const result = await response.json();

            if (result.candidates && result.candidates.length > 0 &&
                result.candidates[0].content && result.candidates[0].content.parts &&
                result.candidates[0].content.parts.length > 0) {
                
                const rawText = result.candidates[0].content.parts[0].text;
                if (isJsonOutput) {
                    try {
                        return JSON.parse(rawText);
                    } catch (parseError) {
                        console.error("Erro ao parsear JSON da IA:", parseError, "Raw text:", rawText);
                        const cleanedJsonText = rawText.replace(/```json\n?/, '').replace(/\n?```/, '').trim();
                        try {
                            return JSON.parse(cleanedJsonText);
                        } catch (finalParseError) {
                             console.error("Erro final ao parsear JSON da IA:", finalParseError);
                             throw new Error("A IA retornou um formato de dados inválido.");
                        }
                    }
                }
                return rawText;
            } else {
                console.error("Resposta inesperada da API Gemini:", result);
                throw new Error("Não foi possível obter uma resposta válida da IA.");
            }
        }

        form.addEventListener('submit', async function(event) {
            event.preventDefault();
            const nicho = nichoInput.value.trim();
            const objetivo = objetivoInput.value.trim();

            if (!nicho || !objetivo) {
                showError("Por favor, preencha os campos de Nicho e Objetivo de Venda.");
                return;
            }

            mensagensContainer.innerHTML = '';
            resultadoDiv.style.display = 'block';
            loadingIndicator.style.display = 'block';
            errorMessageDiv.style.display = 'none';
            copyAllButton.style.display = 'none';
            analyzeToneButton.style.display = 'none';
            toneAnalysisResultDiv.style.display = 'none';
            submitButton.disabled = true;
            submitButton.classList.add('opacity-75', 'cursor-not-allowed');
            resultadoDiv.scrollIntoView({ behavior: 'smooth', block: 'start' });

            try {
                const prompt = `Você é um copywriter especialista em vendas para WhatsApp com uma abordagem moderna e direta.
Crie um script de vendas de 10 mensagens para WhatsApp X1 (conversa individual).
O nicho de mercado é: "${nicho}".
O objetivo principal da venda é: "${objetivo}".
Os mensagens devem ser concisas, claras e persuasivas, incluindo placeholders CLAROS como [EXEMPLO DE PLACEHOLDER EM MAIÚSCULAS].
Retorne o script como um array JSON de 10 strings, onde cada string é uma mensagem.`;
                
                const scriptMessages = await callGeminiAPI(prompt, true);

                if (Array.isArray(scriptMessages) && scriptMessages.length === 10 && scriptMessages.every(m => typeof m === 'string')) {
                    currentScriptMessages = scriptMessages;
                    displayMessages(scriptMessages);
                    copyAllButton.style.display = 'flex';
                    analyzeToneButton.style.display = 'flex';
                } else {
                    throw new Error("A IA não retornou um script no formato esperado (array de 10 mensagens).");
                }

            } catch (error) {
                console.error('Erro ao gerar script:', error);
                showError(error.message || "Ocorreu um erro desconhecido ao gerar o script.");
            } finally {
                loadingIndicator.style.display = 'none';
                submitButton.disabled = false;
                submitButton.classList.remove('opacity-75', 'cursor-not-allowed');
            }
        });

        function displayMessages(messages) {
            mensagensContainer.innerHTML = '';
            messages.forEach((msg, index) => {
                const variationsContainerId = `variations-${index}`;
                const variationButtonId = `varbtn-${index}`;

                const messageWrapper = document.createElement('div');
                // Adiciona a classe base para todos os balões e a específica para enviado
                messageWrapper.classList.add('message-bubble-modern', 'message-sent-modern', 'relative', 'flex', 'flex-col', 'items-end');
                
                let formattedMsg = msg.replace(/\n/g, '<br>');
                formattedMsg = formattedMsg.replace(/(\[[A-ZÁÉÍÓÚÀÂÊÔÇÑ\s0-9_/-]+\])/g, '<strong class="placeholder-highlight-modern px-1 rounded">$1</strong>');


                messageWrapper.innerHTML = `
                    <div class="w-full text-left">
                        <p class="text-xs message-header-modern mb-1">Mensagem ${index + 1}</p>
                        <p class="text-sm">${formattedMsg}</p>
                    </div>
                    <button id="${variationButtonId}" data-index="${index}" data-original-msg="${encodeURIComponent(msg)}"
                            class="mt-2 text-xs variation-button-modern hover:bg-opacity-75 py-1 px-2.5 rounded-full shadow-sm transition-colors duration-150 ease-in-out self-start">
                        Gerar Variação ✨
                    </button>
                    <div id="${variationsContainerId}" class="w-full mt-2 space-y-1.5 variations-container max-h-32 overflow-y-auto pr-1"></div>
                `;
                mensagensContainer.appendChild(messageWrapper);

                document.getElementById(variationButtonId).addEventListener('click', handleGenerateVariation);
            });
        }
        
        async function handleGenerateVariation(event) {
            const button = event.currentTarget;
            const index = button.dataset.index;
            const originalMsg = decodeURIComponent(button.dataset.originalMsg);
            const nicho = nichoInput.value.trim();
            const objetivo = objetivoInput.value.trim();
            const variationsContainer = document.getElementById(`variations-${index}`);
            
            button.innerHTML = 'Gerando... <div class="small-loader"></div>';
            button.disabled = true;

            try {
                const promptVariation = `Você é um assistente de copywriting com foco em comunicação moderna e eficaz. Dada a seguinte mensagem original de um script de vendas para WhatsApp:
Mensagem Original: "${originalMsg}"
Nicho do script: "${nicho}"
Objetivo do script: "${objetivo}"
Gere 1 variação concisa, criativa e direta para esta mensagem, mantendo o mesmo propósito e placeholders se houver.
Retorne a variação como um array JSON que contenha uma única string. Exemplo: ["Nova variação moderna da mensagem."].`;

                const variations = await callGeminiAPI(promptVariation, true);
                
                variationsContainer.innerHTML = ''; 
                if (Array.isArray(variations) && variations.length > 0) {
                    variations.forEach(variationText => {
                        if (typeof variationText === 'string') {
                            const variationDiv = document.createElement('div');
                            // Adiciona a classe base e a específica para variação
                            variationDiv.classList.add('message-bubble-modern', 'variation-bubble-modern', 'p-2', 'text-left');
                            
                            let formattedVariation = variationText.replace(/\n/g, '<br>');
                            formattedVariation = formattedVariation.replace(/(\[[A-ZÁÉÍÓÚÀÂÊÔÇÑ\s0-9_/-]+\])/g, '<strong class="placeholder-highlight-modern px-1 rounded">$1</strong>');
                            variationDiv.innerHTML = formattedVariation;
                            variationsContainer.appendChild(variationDiv);
                        }
                    });
                } else {
                    variationsContainer.innerHTML = '<p class="text-xs text-gray-500 text-left">Nenhuma variação gerada.</p>';
                }
            } catch (error) {
                console.error(`Erro ao gerar variação para msg ${index}:`, error);
                variationsContainer.innerHTML = `<p class="text-xs text-red-400 text-left">Erro ao gerar. Tente novamente.</p>`;
            } finally {
                button.innerHTML = 'Gerar Variação ✨';
                button.disabled = false;
            }
        }

        analyzeToneButton.addEventListener('click', async function() {
            if (currentScriptMessages.length === 0) {
                showError("Gere um script primeiro para analisar o tom.");
                return;
            }

            toneAnalysisResultDiv.style.display = 'block';
            toneLoadingIndicator.style.display = 'inline-block';
            toneAnalysisText.textContent = '';
            analyzeToneButton.disabled = true;
            analyzeToneButton.classList.add('opacity-50');

            try {
                const scriptCompleto = currentScriptMessages.map((msg, i) => `Mensagem ${i+1}: ${msg}`).join("\n");
                const nicho = nichoInput.value.trim();
                const objetivo = objetivoInput.value.trim();

                const promptTone = `Analise o tom geral do seguinte script de vendas para WhatsApp, com foco em uma comunicação moderna:
Nicho: "${nicho}"
Objetivo: "${objetivo}"
Script:
${scriptCompleto}

Descreva o tom predominante (ex: direto e prático, amigável e moderno, persuasivo e arrojado, etc.) e forneça uma breve justificativa (1-2 frases).
Retorne o análise como um objeto JSON com a clave "analise_tom". Exemplo: {"analise_tom": "O tom é X porque Y."}`;

                const analysisResult = await callGeminiAPI(promptTone, true);

                if (analysisResult && typeof analysisResult.analise_tom === 'string') {
                     toneAnalysisText.textContent = analysisResult.analise_tom;
                } else {
                    throw new Error("O análise de tom não retornou o formato esperado.");
                }

            } catch (error) {
                console.error('Erro ao analisar tom:', error);
                toneAnalysisText.textContent = `Erro ao analisar o tom: ${error.message}`;
            } finally {
                toneLoadingIndicator.style.display = 'none';
                analyzeToneButton.disabled = false;
                analyzeToneButton.classList.remove('opacity-50');
            }
        });
        
        function showError(message) {
            errorMessageDiv.querySelector('span.block').textContent = message;
            errorMessageDiv.style.display = 'block';
            loadingIndicator.style.display = 'none';
        }

        copyAllButton.addEventListener('click', function() {
            const messagesToCopy = currentScriptMessages.map((msg, index) => {
                return `Mensagem ${index + 1}:\n${msg}`;
            }).join('\n\n---\n\n');

            const textarea = document.createElement('textarea');
            textarea.value = messagesToCopy;
            document.body.appendChild(textarea);
            textarea.select();
            try {
                document.execCommand('copy');
                const originalButtonText = copyAllButton.innerHTML;
                const checkIconSVG = `
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                    </svg> Copiado!`;
                copyAllButton.innerHTML = checkIconSVG;
                // Mantendo as classes do modern-button-secondary, apenas mudando o texto e talvez a cor do texto/ícone se necessário
                copyAllButton.classList.add('text-emerald-400'); // Feedback visual de sucesso
                copyAllButton.classList.remove('text-emerald-500');


                setTimeout(() => {
                    copyAllButton.innerHTML = originalButtonText;
                    copyAllButton.classList.add('text-emerald-500');
                    copyAllButton.classList.remove('text-emerald-400');
                }, 2000);
            } catch (err) {
                console.error('Erro ao copiar mensagens:', err);
                alert('Não foi possível copiar as mensagens. Tente manualmente.');
            }
            document.body.removeChild(textarea);
        });

    </script>
</body>
</html>
